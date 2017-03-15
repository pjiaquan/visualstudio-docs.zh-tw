---
title: "逐步解說：使用分析工具 API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "效能工具, 逐步解說"
  - "程式碼剖析工具, 逐步解說"
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 逐步解說：使用分析工具 API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

為了示範 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具 API 的用法，本逐步解說會使用 C\# 應用程式。  您可以使用程式碼剖析工具 API 限制在檢測程式碼分析期間所收集的資料量。  
  
 本逐步解說中的步驟通常適用於 C\/C\+\+ 應用程式。  針對每個語言，您必須適當地設定建置環境。  
  
 一般來說，您會從使用取樣分析來開始分析應用程式效能。  如果取樣分析無法提供準確指出瓶頸的資訊，檢測分析可以提供更進一步的詳細資料。  對於調查執行緒的互動，檢測分析非常有用。  
  
 然而，進一步的詳細資料意味著收集的資料也就更多。  所以您可能發現檢測分析會建立大量的資料檔案。  同時，檢測也比較會影響應用程式的效能。  如需詳細資訊，請參閱 [認識檢測資料值](../profiling/understanding-instrumentation-data-values.md)和 [認識取樣資料值](../profiling/understanding-sampling-data-values.md)。  
  
 Visual Studio 分析工具可以讓您限制資料的收集。  本逐步解說提供範例說明如何藉由使用剖析工具 API 限制資料收集。  Visual Studio 分析工具提供在應用程式內控制資料收集的 API。  
  
 針對機器碼，Visual Studio 分析工具 API 位於 VSPerf.dll。  而標頭檔 VSPerf.h 和匯入程式庫 VSPerf.lib，則位於 Microsoft Visual Studio 9\\Team Tools\\Performance Tools 目錄中。  
  
 針對 Managed 程式碼，分析工具 API 位於 Microsoft.VisualStudio.Profiler.dll。  這個 DLL 可於 Microsoft Visual Studio 9\\Team Tools\\Performance Tools 目錄中找到。  如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Profiler>。  
  
## 必要條件  
 本逐步解說假設您選擇的開發環境是設定為支援偵錯和取樣。  下列主題提供這些必要條件的概觀：  
  
 [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)  
  
 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)  
  
 根據預設，啟動程式碼剖析工具時，剖析工具會在全域層級收集資料。  程式開頭的下列程式碼會關閉全域剖析。  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 您可以在命令列關閉資料收集，而不必使用 API 呼叫。  下列步驟假設您的命令列建置環境，是設定為可以執行程式碼剖析工具且可做為您的開發工具。  這包括 VSInstr 和 VSPerfCmd 所需的設定。  請參閱命令列程式碼剖析工具。  
  
## 使用分析工具 API 限制資料收集  
  
#### 若要建立分析的程式碼  
  
1.  根據您的偏好，在 Visual Studio 中或使用命令列建置來建立新的 C\# 專案。  
  
    > [!NOTE]
    >  您的建置必須參考位於 Microsoft Visual Studio 9\\Team Tools\\Performance Tools 目錄中的 Microsoft.VisualStudio.Profiler.dll 程式庫。  
  
2.  將下列程式碼複製並貼入專案中：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### 若要在 Visual Studio IDE 中收集並檢視資料  
  
1.  開啟 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE。  在 \[**分析**\] 功能表上，指向 \[**程式碼剖析工具**\]，然後選取 \[**新增效能工作階段**\]。  
  
2.  將編譯過的二進位檔加入到 \[**效能總管**\] 視窗中的 \[**目標**\] 清單。  以滑鼠右鍵按一下 \[**目標**\]，然後選取 \[**加入目標二進位檔**\]。  在 \[**加入目標二進位檔**\] 對話方塊中找到二進位檔，然後按一下 \[**開啟**\]。  
  
3.  從 \[**效能總管**\] 工具列上的 \[**方法**\] 清單中選取 \[**檢測**\]。  
  
4.  按一下 \[**啟動並啟用程式碼剖析**\]。  
  
     程式碼剖析工具就會進行檢測，並執行二進位檔和建立效能報告檔。  效能報告檔會出現在 \[**效能總管**\] 的 \[**報告**\] 節點中。  
  
5.  開啟結果效能報告檔。  
  
 根據預設，啟動程式碼剖析工具時，剖析工具會在全域層級收集資料。  程式開頭的下列程式碼會關閉全域剖析。  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### 若要在命令列收集並檢視資料  
  
1.  針對在本逐步解說稍早的「若要建立分析的程式碼」程序中建立的範例程式碼，進行偵錯版本的編譯。  
  
2.  若要剖析 Managed 應用程式，請輸入下列命令，以設定適當的環境變數：  
  
     VsPefCLREnv \/traceon  
  
3.  輸入下列命令：VSInstr \<filename\>.exe  
  
4.  輸入下列命令：VSPerfCmd \/start:trace \/output:\<filename\>.vsp  
  
5.  輸入下列命令：VSPerfCmd \/globaloff  
  
6.  執行程式。  
  
7.  輸入下列命令：VSPerfCmd \/shutdown  
  
8.  輸入下列命令：VSPerfReport \/calltrace:\<filename\>.vsp  
  
     在目前的目錄中會建立具有結果效能資料的 .csv 檔案。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Visual Studio 分析工具 API 參考 \(原生\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [使用者入門](../profiling/getting-started-with-performance-tools.md)   
 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)