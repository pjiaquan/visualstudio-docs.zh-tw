---
title: "效能總管視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performanceexplorer"
  - "vs.performance.explorer"
helpviewer_keywords: 
  - "效能工具, 效能總管"
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# 效能總管視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\) 中的 \[**效能總管**\] 視窗可讓您利用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具來設定及啟動效能工作階段。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## 效能總管工具列  
 \[**效能總管**\] 工具列中包含下列選項：  
  
-   **啟動效能精靈** \- 顯示 \[效能精靈\]，以便將新效能工作階段加入至 \[效能總管\] 視窗。  
  
-   **新增效能工作階段** \- 將空白的效能工作階段加入至 \[效能總管\] 視窗。  
  
-   **啟動** \- \[**啟動**\] 命令按鈕清單可讓您啟動目標應用程式，並立即啟用程式碼剖析 \(\[**啟動並啟用程式碼剖析**\]\) 或是暫停程式碼剖析 \(\[**啟動並暫停程式碼剖析**\]\)。  
  
-   **方法** \- 指定工作階段採用的程式碼剖析方法是取樣還是檢測。  
  
-   **停止** \- 立即結束目標應用程式和程式碼剖析工具。  
  
-   **附加\/中斷連結** \- 顯示 \[**將程式碼剖析工具附加至處理序**\] 對話方塊，以選取要附加分析工具的執行中處理序 \(Process\)。  
  
## 效能總管視窗  
 \[**效能總管**\] 視窗包含樹狀目錄控制項，其中顯示一個或多個效能工作階段的二進位檔和報告資料檔案。  
  
-   **工作階段名稱** \- 樹狀目錄控制項的根目錄包含工作階段的名稱。  以滑鼠右鍵按一下工作階段名稱，即可設定工作階段屬性或啟動目標應用程式和程式碼剖析工具。  
  
-   **目標** \- 顯示要在工作階段中進行程式碼剖析的二進位檔之名稱。  以滑鼠右鍵按一下 \[**目標**\] 即可加入或移除二進位檔、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案或網站。  以滑鼠右鍵按一下目標名稱則可設定個別二進位檔的屬性。  
  
-   **報告** \- 顯示工作階段產生之程式碼剖析資料檔案的名稱。  以滑鼠右鍵按一下 \[**報告**\] 即可加入現有的報告或比較兩個程式碼剖析工具資料檔案。  以滑鼠右鍵按一下報告名稱則可開啟、移除或匯出程式碼剖析工具資料檔案。  
  
## 請參閱  
 [概觀](../profiling/overviews-performance-tools.md)   
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [控制資料收集](../profiling/controlling-data-collection.md)