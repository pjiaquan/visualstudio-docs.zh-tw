---
title: "從命令列使用程式碼剖析方法收集效能資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 從命令列使用程式碼剖析方法收集效能資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您會依據幾項因素選擇 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具和選項，這些因素包括進行程式碼剖析的應用程式類型、要使用的程式碼剖析方法，以及目標應用程式是以機器碼或 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 程式碼撰寫。  
  
 本主題根據您選擇的程式碼剖析方法組織命令列程序性主題。  
  
## 本主題內容  
 [用來收集的取樣方法來收集效能統計資料](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [用來收集檢測方法的詳細執行時間資料。](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [使用 .NET 物件記憶體的方法收集記憶體配置和存留期資料](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [使用執行緒並行方法收集資源爭用和活動資料。](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [加入階層互動資料加入至程式碼剖析](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> 用來收集的取樣方法來收集效能統計資料  
 程式碼剖析工具取樣方法會在執行程式碼剖析期間，依照指定的時間間隔收集效能資料。  取樣資料可讓您深入了解 CPU\-bound 效能問題，而且是開始探索應用程式效能的好方法。  
  
 您可以同時啟動程式碼剖析工具和應用程式，或是將程式碼剖析工具附加至正在執行的應用程式執行個體。  
  
|工作|目標應用程式類型|  
|--------|--------------|  
|**啟動應用程式**|-   [獨立應用程式](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [原生獨立應用程式](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Application%20Statistics%20by%20Using%20the%20Command%20Line.md)<br />-   [ASP.NET Web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [原生服務](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> 用來收集檢測方法的詳細執行時間資料。  
 程式碼剖析工具檢測方法會從應用程式二進位檔的複本收集效能資料，這些二進位檔包含記錄效能資訊的軟體探查。  檢測資料是在每一個檢測的函式開始和結束時，以及每一次從檢測的函式呼叫其他函式時收集。  檢測方法對於發現包含 I\/O 問題的效能問題而言相當實用，例如磁碟使用情況。  
  
 您使用 [VInstr.exe](../profiling/vsinstr.md) 工具建立檢測的二進位檔。  初始化程式碼剖析工具之後，會在您執行目標應用程式時，自動從檢測的二進位檔收集資料。  
  
 **目標應用程式類型**  
  
-   [.NET Framework 獨立元件](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [原生獨立元件](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [靜態編譯的 ASP.NET Web 應用程式](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [動態編譯的 ASP.NET Web 應用程式](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)  
  
-   [.NET 服務](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [原生服務](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> 使用 .NET 物件記憶體的方法收集記憶體配置和存留期資料  
 程式碼剖析工具 .NET 記憶體方法可讓您收集 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 記憶體配置資料，以及 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中物件存留期的相關資訊。  
  
 您可以使用分析工具來啟動目標應用程式、將分析工具附加至正在執行的應用程式執行個體，以及建立檢測的應用程式版本，一併收集詳細的執行時間資訊與 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 記憶體資料。  
  
|工作|目標應用程式類型|  
|--------|--------------|  
|**啟動應用程式**|-   [獨立 .NET Framework 應用程式](../Topic/How%20to:%20Launch%20a%20Stand-Alone%20.NET%20Framework%20Application%20with%20the%20Profiler%20to%20Collect%20Memory%20Data%20by%20Using%20the%20Command%20Line.md)|  
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [ASP.NET Web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**檢測模組**|-   [.NET Framework 獨立元件](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [靜態編譯的 ASP.NET Web 應用程式](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [動態編譯的 ASP.NET Web 應用程式](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [.NET 服務](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> 使用執行緒並行方法收集資源爭用和活動資料。  
 程式碼剖析工具並行方法可讓您從多執行緒應用程式收集資源爭用和執行緒與處理序活動資料。  
  
 您可以使用程式碼剖析工具啟動應用程式，或是將程式碼剖析工具附加至正在執行的應用程式執行個體。  
  
|工作|目標應用程式類型|  
|--------|--------------|  
|**啟動應用程式**|-   [獨立 .NET Framework 應用程式](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [獨立原生應用程式](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20.NET%20Framework%20Stand-Alone%20Application%20to%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [原生獨立應用程式](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [ASP.NET Web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [原生服務](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> 加入階層互動資料加入至程式碼剖析  
 加入階層互動資料加入至程式碼剖析要求與命令列程式碼剖析工具的特定程序。  請參閱 [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。  
  
## 請參閱  
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)