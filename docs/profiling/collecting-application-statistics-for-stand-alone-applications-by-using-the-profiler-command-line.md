---
title: "使用分析工具命令列以收集獨立應用程式的應用程式統計資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "取樣分析方法"
  - "分析工具, 取樣方法"
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用分析工具命令列以收集獨立應用程式的應用程式統計資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節說明從命令列使用取樣方法收集用戶端 \(獨立\) 應用程式之效能統計資料的程序和選項。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**使用程式碼剖析來啟動應用程式**|-   [如何：啟動獨立應用程式並收集應用程式統計資料](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**若要將程式碼剖析工具附加至執行中的 .NET Framework 應用程式**|-   [如何：將程式碼剖析工具附加至 .NET Framework 應用程式並收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**將分析工具附加至執行中的 C\/C\+\+ 應用程式**|-   [如何：將程式碼剖析工具附加至原生應用程式並收集應用程式統計資料](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Application%20Statistics%20by%20Using%20the%20Command%20Line.md)|  
|**加入階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## 相關工作  
  
### 對獨立應用程式進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**檢測應用程式**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**收集 .NET 記憶體配置和記憶體回收資料**|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**收集資源爭用與執行緒執行資料**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### 使用取樣方法進行剖析  
  
|工作|相關內容|  
|--------|----------|  
|**對 ASP.NET Web 應用程式進行程式碼剖析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**程式碼剖析服務**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md).  描述如何使用取樣方法，收集 Windows 服務中的效能統計資料。|  
  
### 分析取樣資料檢視與報表  
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)