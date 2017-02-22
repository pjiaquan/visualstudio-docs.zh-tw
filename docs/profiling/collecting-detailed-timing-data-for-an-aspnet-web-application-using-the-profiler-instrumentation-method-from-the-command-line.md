---
title: "從命令列使用程式碼剖析工具檢測方法以收集 ASP.NET Web 應用程式的詳細計時資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "檢測分析方法"
  - "程式碼剖析工具, 檢測方法"
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 從命令列使用程式碼剖析工具檢測方法以收集 ASP.NET Web 應用程式的詳細計時資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節說明使用 **VSPerfCmd** 命令列工具和檢測方法收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式詳細效能資料的程序和選項。  
  
> [!NOTE]
>  **VSPerfCmd** 工具可讓您存取完整的「程式碼剖析工具」功能，包括暫停和繼續進行程式碼剖析，以及從處理器和 Windows 效能計數器收集其他資料。  當您不需要這項功能時，還可以使用 **VSPerfASPNETCmd** 命令列工具。   使用方式比 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具簡單，因為您不必設定環境變數，也不需要重新啟動電腦。  如需詳細資訊，請參閱[使用 VSPerfASPNETCmd 快速進行網站程式碼剖析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**對靜態編譯的二進位檔案進行程式碼剖析**|-   [如何：檢測靜態編譯的 ASP.NET 應用程式並收集詳細計時資料](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**對動態編譯的二進位檔案進行程式碼剖析**|-   [如何：檢測動態編譯的 ASP.NET 應用程式並收集詳細計時資料](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)|  
  
## 相關工作  
  
### 為 ASP.NET Web 應用程式進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**使用取樣方法進行程式碼剖析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**對記憶體配置和記憶體回收進行程式碼剖析**|-   [收集記憶體資料](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**對資源爭用與執行緒活動進行程式碼剖析**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### 使用檢測方法進行剖析  
  
|工作|相關內容|  
|--------|----------|  
|**對獨立 \(用戶端\) 應用程式進行程式碼剖析**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**程式碼剖析服務**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### 分析檢測資料檢視與報表  
 [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)