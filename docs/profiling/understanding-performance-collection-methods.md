---
title: "認識程式碼剖析方法 | Microsoft Docs"
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
  - "vs.performance.wizard.methodpage"
helpviewer_keywords: 
  - "程式碼剖析工具，程式碼剖析方法"
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 認識程式碼剖析方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

The Visual Studio 程式碼剖析工具提供五個可用來收集效能資料的方法。  本主題描述不同的方法並提出特定方法適合用來收集資料的一些情節。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
|方法|描述|  
|--------|--------|  
|[取樣](#sampling)|收集有關應用程式所執行之工作的統計資料。|  
|[檢測](#instrumentation)|收集有關每個函式呼叫的詳細計時資訊。|  
|[並行](#concurrency)|收集多執行緒應用程式的詳細資訊。|  
|[.NET 記憶體](#net_memory)|收集 .NET 記憶體配置和記憶體回收的詳細資訊。|  
|[階層互動](#tier_interaction)|收集有關 SqlServer 資料庫之同步 ADO.NET 函式呼叫的資訊。<br /><br /> 使用 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 或 [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]，階層互動分析可以被收集。  不過，階層互動分析資料只能在 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 或 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 中檢視。|  
  
 您也可以使用部分程式碼剖析方法來收集其他資料，例如軟體和硬體效能計數器。  如需詳細資訊，請參閱[收集其他效能資料](../profiling/collecting-additional-performance-data.md)。  
  
##  <a name="sampling"></a> 取樣  
 取樣程式碼剖析方法會收集應用程式在程式碼剖析回合期間所執行之工作的統計資料。  取樣方法為輕量型，對應用程式方法的執行所造成的影響很小。  
  
 取樣是Visual Studio程式碼剖析工具的預設方法。  這種方法適用於下列工作：  
  
-   初始探索應用程式的效能。  
  
-   調查涉及處理器 \(CPU\) 使用率的效能問題。  
  
 取樣程式碼剖析方法會定期中斷電腦處理器，並收集函式呼叫堆疊。  專有樣本計數是針對執行中的函式而遞增，內含計數則是針對呼叫堆疊上的所有呼叫函式而遞增。  取樣報表會依照程式碼剖析的模組、函式、原始程式碼行及指令呈現這些計數的總計。  
  
 根據預設，分析工具將取樣間隔設為 CPU 週期。  您可以將間隔類型變更為另一個 CPU 效能計數器，也可以設定間隔的計數器事件數目。  您也可以收集階層互動分析 \(TIP\) 資料，以便提供透過 ADO.NET 對 SQL Server 資料庫所發出之查詢的相關資訊。  
  
 [使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
 [認識取樣資料值](../profiling/understanding-sampling-data-values.md)  
  
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)  
  
##  <a name="instrumentation"></a> 檢測  
 檢測程式碼剖析方法會對進行程式碼剖析的應用程式中的函式呼叫收集詳細的計時資訊。  檢測程式碼剖析適用於下列工作：  
  
-   調查輸入\/輸出瓶頸，例如磁碟 I\/O。  
  
-   完整檢查特定模組或一組函式。  
  
 檢測方法會在二進位檔中插入程式碼，為受檢測檔案中的每個函式以及這些函式所發出的每個函式呼叫擷取計時資訊。  檢測也會識別函式何時呼叫作業系統以執行作業，例如寫入檔案。  檢測報表使用四個值來表示花在函式或原始程式碼行的總時間：  
  
-   整體內含 \- 執行函式或原始程式行所花費的總時間。  
  
-   應用內含 \- 執行函式或原始程式行所花費的時間，但不包括呼叫作業系統所花費的時間。  
  
-   整體專有 \- 執行函式或原始程式碼行之主體中的程式碼所花費的時間。  執行函式或原始程式行所呼叫之函式所花費的時間則排除在外。  
  
-   應用專有 \- 執行函式或原始程式碼行之主體中的程式碼所花費的時間。  執行作業系統呼叫所花費的時間，以及執行函式或原始程式行所呼叫之函式所花費的時間則排除在外。  
  
 您也可以使用檢測方法收集 CPU 和軟體效能計數器。  
  
 [認識檢測資料值](../profiling/understanding-instrumentation-data-values.md)  
  
 [使用檢測收集計時詳細資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
 [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)  
  
##  <a name="concurrency"></a> 並行  
 並行程式碼剖析會收集多執行緒應用程式的詳細資訊。  資源爭用程式碼剖析會在每次競爭的執行緒被迫等候存取共用資源時收集詳細呼叫堆疊資訊。  並行視覺化也會收集有關多執行緒應用程式與其本身、硬體、作業系統和主機電腦上其他處理序互動方式的一般資訊。  
  
-   資源爭用報表會顯示爭用總數，以及發生等候之模組、函式、原始程式碼行和指令等候資源所花費的總時間。  發生爭用時，時間表圖形也會加以顯示。  
  
-   並行視覺化檢視會顯示圖形資訊，您可以使用此資訊找出效能瓶頸、CPU 使用率不彰、執行緒爭用、執行緒移轉、同步處理延遲、I\/O 重疊區域及其他資訊。  可能的話，圖形輸出會連結至呼叫堆疊和原始程式碼資料。  並行視覺化資料只能針對命令列和 Windows 應用程式進行收集。  
  
 [認識資源爭用資料值](../profiling/understanding-resource-contention-data-values.md)  
  
 [收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
 [資源爭用資料檢視](../profiling/resource-contention-data-views.md)  
  
 [並行視覺化檢視](../profiling/concurrency-visualizer.md)  
  
##  <a name="net_memory"></a> .NET 記憶體  
 每次在進行程式碼剖析的應用程式中配置 .NET Framework 物件時，.NET 記憶體配置的程式碼剖析方法都會中斷電腦處理器。  如果同時收集物件存留期資料，則分析工具會在每次 .NET Framework 記憶體回收後中斷處理器。  
  
 分析工具會收集在配置中建立或在記憶體回收中終結之物件類型、大小和數目的相關資訊。  
  
-   發生配置事件時，分析工具會收集函式呼叫堆疊的其他資訊。  專有配置計數是針對目前執行中的函式而遞增，內含計數則是針對呼叫堆疊上的所有呼叫函式而遞增。.NET 報表會依照程式碼剖析的型別、模組、函式、原始程式碼行及指令呈現這些計數的總計。  
  
-   發生記憶體回收時，分析工具會收集終結之物件的資料，以及在每個記憶體回收層代中之物件的相關資訊。  在執行程式碼剖析結束時，分析工具會記錄尚未明確終結之物件的資料。  物件存留期報表會顯示在執行程式碼剖析期間所配置每個型別的合計。  
  
 .NET 記憶體程式碼剖析可以在取樣或檢測模式中使用。  選取的模式不會影響 .NET 記憶體程式碼剖析獨有的配置和物件存留期報表：  
  
-   以取樣模式執行 .NET 記憶體程式碼剖析時，分析工具會將記憶體配置事件當做間隔，並且顯示配置的物件數目和配置的總位元組數目做為報表中的內含和專有值。  
  
-   以檢測模式執行 .NET 記憶體程式碼剖析時，則會收集詳細的計時資訊，以及內含和專有配置值。  
  
 [認識記憶體配置和物件存留期資料值](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
 [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)  
  
##  <a name="tier_interaction"></a> 階層互動  
 階層互動分析會將有關 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 網頁或其他應用程式和 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫之間同步 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 呼叫的資訊加入至程式碼剖析資料檔案。  資料包含呼叫數目和時間，以及最多和最少次數。  階層互動資料可以加入至透過取樣、檢測、.NET 記憶體或並行方法所收集的程式碼剖析資料。  
  
 ![階層互動分析資料](../profiling/media/tierinteraction_profilingtools.png "TierInteraction\_ProfilingTools")  
程式碼剖析工具所收集的階層互動資料  
  
 [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)  
  
 [階層互動檢視](../profiling/tier-interaction-views.md)  
  
## 請參閱  
 [如何：使用效能精靈對網站或 Web 應用程式進行程式碼剖析](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [效能分析的初級開發人員指南](../profiling/beginners-guide-to-performance-profiling.md)