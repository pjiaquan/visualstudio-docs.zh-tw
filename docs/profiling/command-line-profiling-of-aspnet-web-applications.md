---
title: "ASP.NET Web 應用程式的命令列分析 | Microsoft Docs"
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
  - "對 ASP.NET 應用程式進行程式碼剖析"
  - "程式碼剖析工具，ASP.NET 應用程式"
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ASP.NET Web 應用程式的命令列分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節說明從命令列使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式效能資料的程序和選項。  
  
> [!NOTE]
>  在 Windows 8 中的增強的安全性功能和 Windows Server 2012 要求 Visual Studio 分析工具會收集這些平台之資料的方式有重大的變更。  Windows 存放區應用程式也需要新的技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**輕鬆地收集基本 ASP.NET 程式碼剖析資料**：使用 **VSPerfASPNETCmd** 工具收集取樣、檢測、.NET 記憶體、爭用或階層互動資料時，沒有任何組態需求，也不必和 **VSPerfCmd** 一樣需要重新啟動網際網路資訊服務 \(IIS\)。  **VSPerfASPNETCmd** 不允許您收集其他資料或控制資料收集。 **Note:**  **VSPerfASPNETCmd** 是建議您在透過獨立分析工具對 ASP.NET 網站進行程式碼剖析時使用的較佳工具。|-   [使用 VSPerfASPNETCmd 快速進行網站程式碼剖析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**收集應用程式統計資料**：使用取樣方法來收集效能統計資料。  取樣資料對分析 CPU 使用率問題以及了解應用程式的一般效能特性很有用。|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**收集詳細的時間資料**：使用檢測方法收集詳細的時間資訊。  檢測資料對 IO 問題分析以及應用程式案例的細部分析很有用。|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**收集 .NET 記憶體資料**：使用取樣或檢測收集顯示已配置物件之大小及數量的 .NET 記憶體配置資料。  您也可以收集物件存留期資料，其中顯示每個記憶體回收層代中所回收的物件大小和數目。|-   [收集記憶體資料](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**收集並行資料**：使用並行方法收集資源爭用資料。 **Note:**  不支援收集 Web 應用程式的執行緒活動及視覺化資料。|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**加入階層互動資料**：您可以加入有關 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式對 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫進行之同步 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 呼叫的效能資料。|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## 相關工作  
  
|工作|相關內容|  
|--------|----------|  
|**對獨立 \(用戶端\) 應用程式進行程式碼剖析**|-   [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**程式碼剖析服務**|-   [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)|