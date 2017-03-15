---
title: "服務的命令列程式碼剖析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼剖析工具，服務"
  - "程式碼剖析服務"
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 服務的命令列程式碼剖析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節說明從命令列使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具收集 Windows 服務之效能資料的程序和選項。  
  
> [!NOTE]
>  在 Windows 8 中的增強的安全性功能和 Windows Server 2012 要求 Visual Studio 分析工具會收集這些平台之資料的方式有重大的變更。  Windows 存放區應用程式也需要新的技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**收集應用程式統計資料**：使用取樣方法來收集效能統計資料。  取樣資料對分析 CPU 使用率問題以及了解應用程式的一般效能特性很有用。|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**收集詳細的時間資料**：使用檢測方法收集詳細的時間資訊。  檢測資料對 IO 問題分析以及應用程式案例的細部分析很有用。|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**收集 .NET 記憶體資料**：使用取樣或檢測收集顯示已配置物件之大小及數量的 .NET 記憶體配置資料。  您也可以收集物件存留期資料，其中顯示每個記憶體回收層代中所回收的物件大小和數目。|-   [收集 .NET 記憶體資料](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**收集並行資料**：使用並行方法收集資源爭用資料，以及收集會顯示 CPU 使用情況、執行緒爭用、執行緒轉換、同步處理延遲、重疊 IO 的區域以及其他系統事件的執行緒活動資料。|-   [收集並行資料](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**加入階層互動資料**：您可以加入有關服務對 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫進行之同步 ADO.NET 呼叫的效能資料。|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## 相關工作  
  
|工作|相關內容|  
|--------|----------|  
|**對獨立 \(用戶端\) 應用程式進行程式碼剖析**|-   [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**對 ASP.NET 應用程式進行程式碼剖析**|-   [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)|