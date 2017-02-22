---
title: "使用程式碼剖析工具命令列收集獨立應用程式的並行資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "並行分析方法"
  - "程式碼剖析工具，並行方法"
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用程式碼剖析工具命令列收集獨立應用程式的並行資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具的並行方法可讓您收集資源爭用資料和執行緒活動資料，其中顯示 CPU 使用率、執行緒爭用、執行緒移轉、同步處理延遲、重疊 IO 的區域以及其他系統事件。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**啟動 .NET Framework 應用程式及對並行資料進行程式碼剖析**|-   [如何：啟動 .NET Framework 應用程式以收集並行資料](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**啟動 C\/C\+\+ 應用程式並對並行資料進行程式碼剖析**|-   [如何：啟動原生應用程式以收集並行資料](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**將程式碼剖析工具附加至執行中的 .NET Framework 應用程式**|-   [如何：將程式碼剖析工具附加至 .NET Framework 應用程式以收集並行資料](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20.NET%20Framework%20Stand-Alone%20Application%20to%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)|  
|**將分析工具附加至執行中的 C\/C\+\+ 應用程式**|-   [如何：將程式碼剖析工具附加至原生應用程式並收集並行資料](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)|  
  
## 相關工作  
  
### 對獨立應用程式進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**使用取樣方法進行程式碼剖析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**使用檢測方法進行程式碼剖析**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**對 .NET 記憶體配置和記憶體回收進行程式碼剖析**|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**加入階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### 對並行問題進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**對 ASP.NET 應用程式進行程式碼剖析**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**程式碼剖析服務**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### 分析並行資料檢視與報表  
 [資源爭用資料檢視](../profiling/resource-contention-data-views.md)  
  
 [並行視覺化檢視](../profiling/concurrency-visualizer.md)  
  
## 參考資料  
 [命令列程式碼剖析工具參考](../profiling/command-line-profiling-tools-reference.md)