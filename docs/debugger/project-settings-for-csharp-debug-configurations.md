---
title: "C# 偵錯組態的專案設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯組建, 專案設定"
  - "偵錯組態, C#"
  - "偵錯組態, J#"
  - "偵錯 [C#], 偵錯工具設定"
  - "偵錯 [J#], 偵錯工具設定"
  - "專案組態, 偵錯"
  - "專案設定 [Visual Studio], 偵錯組態"
  - "專案 [Visual Studio], 偵錯組態"
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C# 偵錯組態的專案設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在 \[**屬性頁**\] 視窗中變更 C\# 偵錯組態的專案設定 \(如[偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)中所討論\)。  下表顯示 \[**屬性頁**\] 視窗中，與偵錯工具相關的設定位置。  
  
> [!WARNING]
>  本主題不適用於 Windows 市集應用程式。  請參閱[啟動偵錯工作階段 \(VB、C\#、C\+\+ 和 XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> 偵錯索引標籤  
  
|**設定值**|**描述**|  
|-------------|------------|  
|**組態**|設定應用程式的編譯模式。  請選擇 \[**現用 \(偵錯\)**\]、\[**偵錯**\]、\[**發行**\] 或 \[**所有組態**\] 其中之一。|  
|**起始動作**|這個控制項群組會指定當您從 \[偵錯\] 功能表選擇 \[啟動\] 時會發生的動作。<br /><br /> -   \[**起始專案**\] 是預設動作，而且會啟動偵錯的啟始專案。  如需詳細資訊，請參閱[選擇啟始專案](http://msdn.microsoft.com/zh-tw/222e3f32-a6fe-4941-bf37-6b2a921129fd)。<br />-   \[**啟動外部程式**\] 讓您可以啟動並附加至不屬於 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案一部分的程式。  如需詳細資訊，請參閱[附加至正在執行的程式](http://msdn.microsoft.com/zh-tw/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)。<br />-   \[**以 URL 啟動瀏覽器**\] 可讓您偵錯 Web 應用程式。|  
|**命令列的引數**|指定要偵錯的程式之命令列引數。  命令名稱是在 \[啟動外部程式\] 指定的程式名稱。  如果 \[啟動動作\] 設為 \[起始 URL\]，便不能指定命令列引數。|  
|**工作目錄**|指定為程式偵錯時的工作目錄。  在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，工作目錄預設為啟動應用程式的來源目錄：\\bin\\debug。|  
|**使用遠端機器**|執行應用程式以進行偵錯的遠端機器名稱，或 [Msvsmon 伺服器名稱](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md)。  遠端機器上 EXE 的位置是從 \[建置\] 分類、\[組態屬性\] 資料夾中的 \[輸出路徑\] 屬性中所指定。  其位置必須是遠端電腦上的可共用目錄。|  
|**啟用 Unmanaged 程式碼偵錯**|讓您可以從 Managed 應用程式偵錯原生 \(Unmanaged\) Win32 程式碼的呼叫。|  
|**啟用 SQL Server 偵錯**|允許 SQL Server 資料庫物件偵錯。|  
  
##  <a name="BKMK_Build_tab"></a> 建置索引標籤  
  
|設定|描述|  
|--------|--------|  
|**條件式編譯的符號:**|此處會定義 DEBUG 和 TRACE 常數。<br /><br /> 這些常數可啟用 [Debug 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx)和 [Trace 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx)的條件式編譯。  完成這些常數定義之後，Debug 和 Trace 類別方法便會於[輸出視窗](../ide/reference/output-window.md)產生輸出。  如果沒有這些常數，Debug 和 Trace 類別方法便不會編譯，且不會產生輸出。<br /><br /> -   Debug 一般會定義在程式的偵錯版本中，而發行版本則不會定義。<br />-   Trace 通常會定義在偵錯版本和發行版本中。|  
|**最佳化程式碼**|除非您發現一個僅出現在最佳化程式碼裡的錯誤，否則您應該在偵錯版本裡關閉這個設定。  因為指令無法直接對應到來源視窗的陳述式，所以較難偵錯最佳化程式碼。|  
|**輸出路徑:**|偵錯通常會設為 bin\\Debug。|  
  
## 請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)