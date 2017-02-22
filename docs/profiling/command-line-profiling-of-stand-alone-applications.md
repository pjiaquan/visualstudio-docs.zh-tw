---
title: "獨立應用程式的命令列分析 | Microsoft Docs"
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
  - "程式碼剖析工具，獨立應用程式"
  - "對獨立應用程式進行程式碼剖析"
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 獨立應用程式的命令列分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節說明從命令列使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具收集獨立 \(用戶端\) 應用程式效能資料的程序和選項。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**收集應用程式統計資料**：使用取樣方法來收集效能統計資料。  取樣資料對分析 CPU 使用率問題以及了解應用程式的一般效能特性很有用。|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**收集詳細的時間資料**：使用檢測方法收集詳細的時間資訊。  檢測資料對 I\/O 問題分析以及應用程式案例的細部分析很有用。|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**收集 .NET 記憶體資料**：使用取樣或檢測收集顯示已配置物件之大小及數量的 .NET 記憶體配置資料。  您也可以收集物件存留期資料，其中顯示每個記憶體回收層代中所回收的物件大小和數目。|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**收集並行資料**：使用並行方法收集資源爭用資料，以及收集會顯示 CPU 使用情況、執行緒爭用、執行緒轉換、同步處理延遲、重疊 I\/O 的區域以及其他系統事件的執行緒活動資料。|-   [收集並行資料](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**加入階層互動資料**：您可以加入有關應用程式對 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫進行之同步 ADO.NET 呼叫的效能資料。  加入階層互動資料加入至程式碼剖析要求與命令列程式碼剖析工具的特定程序。|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**實際操作**：透過逐步程序，使用取樣或檢測方法對範例用戶端應用程式進行程式碼剖析。|-   [逐步解說：使用取樣進行命令列剖析](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)<br />-   [逐步解說：使用檢測進行命令列剖析](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## 相關工作  
  
|工作|相關內容|  
|--------|----------|  
|**對 ASP.NET 應用程式進行程式碼剖析**|-   [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**程式碼剖析服務**|-   [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)|