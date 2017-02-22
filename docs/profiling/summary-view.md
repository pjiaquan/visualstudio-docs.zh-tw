---
title: "摘要檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.summary"
helpviewer_keywords: 
  - "效能報告, 摘要檢視"
  - "程式碼剖析工具報告, 摘要檢視"
  - "程式碼剖析工具, 摘要檢視"
  - "摘要檢視"
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 摘要檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[摘要\] 檢視會顯示執行程式碼剖析時，高度耗費效能之函式或物件的相關資訊。  此檢視提供時間表圖形與兩個或多個耗費最多資源的函式或物件清單 \(根據程式碼剖析方法的效能標準\)。  在此檢視中的資料取決於所使用的程式碼剖析方法 \(取樣、檢測或並行\)，以及是否有收集到 .NET 記憶體配置。  
  
 在所有的 \[摘要\] 檢視 \(並行資料中的 \[摘要\] 檢視除外\)，\[摘要\] 檢視中的時間表都會顯示在發生程式碼剖析的一段時間，進行程式碼剖析之應用程式的處理器 \(CPU\) 使用率。  
  
-   如果在圖形上指定時間區段，就可以重新分析該區段的資料，或是將時間表顯示放大到您所指定的區段。  如需詳細資訊，請參閱[如何：從摘要時間表篩選報表檢視](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
-   您可以按一下 \[摘要\] 檢視清單中的函式，以開啟該函式的 \[函式詳細資料\] 檢視。  您也可以以滑鼠右鍵按一下函式以使用其他檢視選項。  
  
-   若要修改出現在 \[摘要\] 檢視清單中的項目數目，請開啟 \[**工具**\] 功能表，並指向\[**選項**\]，然後按一下\[**效能工具**\]。  在 \[**一般設定**\] 下，修改 \[**摘要檢視中的函式數目**\] 設定。  
  
## 通知連結  
 您可以按一下 \[通知\] 清單中的連結，設定報告的顯示選項。  清單在時間表圖形的右邊。  
  
|||  
|-|-|  
|**顯示非使用者程式碼**<br /><br /> **只顯示我的程式碼**|沒有提供給原生程式碼，或是使用檢測方法所收集到的分析資料。  在只顯示使用者程式碼的資料 \(**\[顯示 Just My Code\]**\) 與顯示包含系統程式碼之所有程式碼的資料 \(**\[顯示非使用者程式碼\]**\) 之間切換。  預設情況下，資料會受限為使用者程式碼。  若變更設定，請參閱 [如何：篩選報表檢視以顯示 Just My Code](../Topic/How%20to:%20Filter%20Profiling%20Tools%20Report%20Views%20to%20Display%20Just%20My%20Code.md)。|  
|**檢視指引**|在 \[**錯誤清單**\] 視窗中顯示效能規則的警告。  如需詳細資訊，請參閱[使用效能規則分析資料](../profiling/using-performance-rules-to-analyze-data.md)。|  
  
## 報表  
 您可以按一下 \[報告\] 清單中的連結開啟不同的檢視，以及比較、 儲存或篩選報告。  清單在時間表圖形的右邊。  
  
|||  
|-|-|  
|**顯示修改過的呼叫樹狀圖**|顯示在呼叫樹狀結構檢視中，耗費最多資源的執行路徑。  如需詳細資訊，請參閱[呼叫樹狀圖檢視](../profiling/call-tree-view.md)。|  
|**顯示熱門程式行**|沒有提供給使用檢測方法收集到的分析資料。  顯示在程式行檢視中，耗費最多資源的原始程式碼。  如需詳細資訊，請參閱[程式行檢視](../profiling/lines-view.md)。|  
|**比較報告**|顯示 \[**選取要進行比較的分析檔案**\] 對話方塊，其中可以指定另一個程式碼剖析資料檔來比較目前的檔案。  如需詳細資訊，請參閱[比較程式碼剖析工具資料檔案](../profiling/comparing-performance-data-files.md)。|  
|**匯出報表資料**|顯示 \[**匯出報告**\] 對話方塊，您可以在其中指定一個或多個報表檢視，將其儲存為逗號分隔值 \(.csv\) 或 .xml 檔案。  如需詳細資訊，請參閱[How to: Export Profiling Tools Reports](http://msdn.microsoft.com/zh-tw/174b5bd3-df9b-4fd4-88d4-76032ab90451)。|  
|**儲存分析過的報表**|將目前的程式碼剖析資料檔案儲存為 .vsps 檔，這樣會更快速地在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面中開啟。  如需詳細資訊，請參閱[How to: Save Analyzed Profiling Data Files](http://msdn.microsoft.com/zh-tw/0340ddde-caf4-48ac-8af3-d15dcdade556)。|  
|**篩選報告資料**|顯示程式碼剖析報告篩選條件窗格，您可以在其中指定準則以限制報告檢視中的資料。  如需詳細資訊，請參閱[程式碼剖析工具報告檢視篩選條件](../profiling/performance-report-view-filter.md)。|  
|**切換全螢幕**|切換報表檢視的全螢幕模式。|  
  
## 請參閱  
 [摘要檢視](../profiling/summary-view-sampling-data.md)   
 [摘要檢視](../profiling/summary-view-instrumentation-data.md)   
 [摘要檢視](../profiling/summary-view-dotnet-memory-data.md)