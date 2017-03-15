---
title: "使用程式碼剖析工具命令列收集 ASP.NET Web 應用程式的記憶體資料 | Microsoft Docs"
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
  - ".NET 記憶體分析方法"
  - "程式碼剖析工具, .NET 記憶體方法"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用程式碼剖析工具命令列收集 ASP.NET Web 應用程式的記憶體資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節說明使用 **VSPerfCmd** 命令列工具收集 ASP.NET Web 應用程式的記憶體配置和物件存留期資料的程序和選項。  
  
> [!NOTE]
>  **VSPerfCmd** 工具可讓您存取完整的「程式碼剖析工具」功能，包括暫停和繼續進行程式碼剖析，以及從處理器和 Windows 效能計數器收集其他資料。  當您不需要這項功能時，還可以使用 **VSPerfASPNETCmd** 命令列工具。   使用方式比 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具簡單，因為您不必設定環境變數，也不需要重新啟動電腦。  如需詳細資訊，請參閱[使用 VSPerfASPNETCmd 快速進行網站程式碼剖析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**將分析工具附加至執行中的 ASP.NET 應用程式**|-   [如何：將程式碼剖析工具附加至 ASP.NET Web 應用程式以收集記憶體資料](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**檢測靜態編譯的二進位檔案**|-   [如何：檢測靜態編譯的 ASP.NET 應用程式並收集記憶體資料](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**檢測動態編譯的二進位檔案**|-   [如何：檢測動態編譯的 ASP.NET 應用程式並收集記憶體資料](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## 相關工作  
  
### 為 ASP.NET Web 應用程式進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**使用取樣方法進行程式碼剖析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**使用檢測方法進行程式碼剖析**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**對資源爭用與執行緒活動進行程式碼剖析**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### 對 .NET Framework 記憶體資料進行程式碼剖析  
  
|工作|相關內容|  
|--------|----------|  
|**對獨立 \(用戶端\) 應用程式進行程式碼剖析**|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**程式碼剖析服務**|-   [收集 .NET 記憶體資料](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### 分析 .NET 記憶體資料檢視與報表  
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)  
  
## 參考資料  
 [命令列程式碼剖析工具參考](../profiling/command-line-profiling-tools-reference.md)