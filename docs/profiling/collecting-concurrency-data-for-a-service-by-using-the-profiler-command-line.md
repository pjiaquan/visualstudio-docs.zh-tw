---
title: "使用程式碼剖析工具命令列收集服務的並行資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 使用程式碼剖析工具命令列收集服務的並行資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具的並行方法可讓您收集資源爭用資料和執行緒活動資料，其中顯示 CPU 使用率、執行緒爭用、執行緒移轉、同步處理延遲、重疊 IO 的區域以及其他系統事件。  
  
> [!NOTE]
>  在 Windows 8 中的增強的安全性功能和 Windows Server 2012 要求 Visual Studio 分析工具會收集這些平台之資料的方式有重大的變更。  Windows 存放區應用程式也需要新的技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**附加至執行中的 .NET 服務**|-   [如何：將程式碼剖析工具附加至 .NET 服務以收集並行資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**加入階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**附加至執行中的 C\/C\+\+ 服務**|-   [如何：將程式碼剖析工具附加至原生服務以收集並行資料](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## 相關工作  
  
### 對 Windows 服務進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**使用取樣方法進行程式碼剖析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**使用檢測方法進行程式碼剖析**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**對 .NET 記憶體配置和記憶體回收進行程式碼剖析**|-   [收集 .NET 記憶體資料](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### 對並行資料進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**對獨立應用程式進行程式碼剖析**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**對 ASP.NET Web 應用程式進行程式碼剖析**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### 分析並行資料檢視與報表  
 [資源爭用資料檢視](../profiling/resource-contention-data-views.md)  
  
 [並行視覺化檢視](../profiling/concurrency-visualizer.md)  
  
## 參考資料  
 [命令列程式碼剖析工具參考](../profiling/command-line-profiling-tools-reference.md)