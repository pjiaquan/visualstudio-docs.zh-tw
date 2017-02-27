---
title: "如何：檢閱、儲存和設定建置記錄檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# 如何：檢閱、儲存和設定建置記錄檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual Studio IDE 後建置專案，您可以檢視該組建的資訊在 \[**輸出**\] 視窗中。  您可以使用這項資訊，您可以，例如，疑難排解建置失敗。  對於 C\+\+ 專案，您也可以檢視在自動建立並儲存的 .txt 檔案的相同資訊。  針對 Managed 程式碼專案，您可以複製及貼上從 \[**輸出**\] 視窗將資訊輸入到 .txt 檔案和儲存自己。  您也可以使用 IDE 指定何種資訊要檢視有關每個組建。  
  
 使用 MSBuild，如果您建立任何類型的專案，您可以建立 .txt 檔案儲存組建的相關資訊。  如需詳細資訊，請參閱[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
### 若要檢視 C \+\+. 的建置記錄檔專案  
  
1.  在 \[**Windows 檔案總管**\] 或 \[**檔案總管**\] 中，開啟下列檔案:\\…  \\ Visual Studio AMPL lT *版本*AMPL gT \\ Projects \\*ProjectName*\\*ProjectName*\\ Debug \\*ProjectName*.txt  
  
### 若要建立 Managed 程式碼的組建記錄檔專案  
  
1.  在功能表列上，選擇 **建置**， **建置方案**。  
  
2.  在 \[**輸出**\] 視窗中，反白顯示從組建的資訊，然後將其複製到剪貼簿。  
  
3.  開啟文字編輯器，例如記事本\)，貼上資訊寫入檔案，然後儲存檔案。  
  
### 變更在建置記錄檔中包含的資訊量  
  
1.  在功能表列上，選擇 \[**工具**\]\]，則 \[**選項**\]。  
  
2.  在 \[**專案和方案**\] 頁面上，選取 \[**建置並執行**\] 頁面。  
  
3.  在 \[**MSBuild 專案建置輸出詳細等級**\] 清單中，選取下列其中一個值，然後選擇 \[**OK**\] 按鈕。  
  
    |詳細等級|描述|  
    |----------|--------|  
    |無訊息|只會顯示組建的摘要。|  
    |最小|顯示組建的摘要和錯誤、被分類為高度和重要的警告訊息。|  
    |Normal|顯示組建的摘要;錯誤、被分類為高度重要的警告和訊息;建置的主要步驟。  您通常會使用這個詳細資料層級。|  
    |詳細|顯示組建的摘要;錯誤、被分類為高度重要的警告和訊息;所有建置步驟;就一般重要性分類的訊息。|  
    |診斷|顯示為組建可用的所有資料。  您可以使用這個詳細資料層級協助偵錯與自訂建置指令碼和其他組建問題的問題。|  
  
     如需詳細資訊，請參閱[選項對話方塊, 專案和方案, 建置和執行](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)與<xref:Microsoft.Build.Framework.LoggerVerbosity>。  
  
    > [!IMPORTANT]
    >  您必須重新建置您的專案可以在 \[**輸出**\] 視窗 \(所有專案\) 和 *ProjectName*.txt 檔案 \(僅限 C\+\+ 專案的作用\)。  
  
## 請參閱  
 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md)