---
title: "使用程式碼剖析工具取樣方法收集服務的應用程式統計資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用程式碼剖析工具取樣方法收集服務的應用程式統計資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節說明從命令列使用取樣方法收集 Windows 服務之效能統計資料的程序和選項。  
  
> [!NOTE]
>  在 Windows 8 中的增強的安全性功能和 Windows Server 2012 要求 Visual Studio 分析工具會收集這些平台之資料的方式有重大的變更。  Windows 存放區應用程式也需要新的技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**將程式碼剖析工具附加至 .NET 服務**|-   [如何：將程式碼剖析工具附加至 .NET 服務以收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**加入階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**將程式碼剖析工具附加至 C\/C\+\+ 服務**|-   [如何：將程式碼剖析工具附加至原生服務以收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## 相關工作  
  
### 對 Windows 服務進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**使用檢測方法進行程式碼剖析**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**對 .NET 記憶體配置和記憶體回收進行程式碼剖析**|-   [收集 .NET 記憶體資料](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**對資源爭用與執行緒活動進行程式碼剖析**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### 使用取樣方法進行剖析  
  
|工作|相關內容|  
|--------|----------|  
|**對獨立 \(用戶端\) 應用程式進行程式碼剖析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**對 ASP.NET Web 應用程式進行程式碼剖析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
  
### 分析取樣資料檢視與報表  
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)