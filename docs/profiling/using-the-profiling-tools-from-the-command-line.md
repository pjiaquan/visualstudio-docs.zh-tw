---
title: "從命令列使用程式碼剖析工具 | Microsoft Docs"
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
  - "命令列，效能工具"
  - "命令列工具，效能工具"
  - "程式碼剖析工具，命令列"
  - "工具，命令列"
  - "命令列，工具"
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 從命令列使用程式碼剖析工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具在命令提示字元對應用程式進行程式碼剖析，以及使用批次檔和程式碼自動化程式碼剖析。  您也可以在命令提示字元產生報告檔。  您可以在沒有安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的電腦上使用輕量型獨立分析工具收集資料。  
  
> [!NOTE]
>  在 Windows 8 中的增強的安全性功能和 Windows Server 2012 要求 Visual Studio 分析工具會收集這些平台之資料的方式有重大的變更。  Windows 存放區應用程式也需要新的技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**設定符號的位置**：若要顯示函式和參數的名稱，分析工具必須能夠存取受剖析之二進位檔的符號檔 \(.pdb\)。  這些檔案應包括您要在分析中檢視之 Microsoft 作業系統和應用程式的符號檔。  您可以使用公用 Microsoft 符號伺服器確定具有 Microsoft 二進位檔的正確 .pdb 檔。|-   [如何：從命令列指定符號檔位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**對應用程式進行程式碼剖析**：用來對目標應用程式進行程式碼剖析的命令列工具和選項，取決於應用程式的類型、程式碼剖析方法，以及目標是 Managed 或原生應用程式而定。|-   [從命令列使用程式碼剖析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)|  
|**建立 .xml 和 .csv 報告**：在命令提示字元進行程式碼剖析會建立資料檔，這些檔案可在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 介面中檢視。  您也可以使用 VSPerfReport 命令列工具產生資料的 .xml 或逗號分隔值檔 \(.csv\)。|-   [從命令列建立程式碼剖析工具報告](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**在沒有 Visual Studio 的電腦上剖析程式碼**：您可以在沒有安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的電腦上使用程式碼剖析工具的獨立分析工具收集應用程式的資料。|-   [如何：安裝獨立分析工具](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## 參考資料  
 [命令列程式碼剖析工具參考](../profiling/command-line-profiling-tools-reference.md)  
  
## 請參閱  
 [使用程式碼剖析工具](../profiling/performance-explorer.md)