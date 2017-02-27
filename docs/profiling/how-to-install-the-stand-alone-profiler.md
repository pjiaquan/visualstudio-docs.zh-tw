---
title: "如何：安裝獨立分析工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "效能工具, 安裝獨立程式碼剖析工具"
  - "程式碼剖析工具, 獨立程式碼剖析工具"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：安裝獨立分析工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供一套命令列架構的獨立分析工具 \(Profiler\)，可以在不安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 的情況下執行。  當電腦沒有或無法安裝開發環境時，就會發生這種情況。  例如，您不能在實際執行的 Web 伺服器上安裝開發環境。  
  
> [!NOTE]
>  使用獨立分析工具收集 ASP.NET 網站的效能資料時，建議優先使用 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 命令列工具，而 [VSPerfCmd](../profiling/vsperfcmd.md) 工具則次之。  
  
### 若要安裝獨立分析工具  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安裝媒體內包含 \\Standalone Profiler 路徑的目錄中，找出獨立分析工具的安裝程式 \(vs\_profiler.exe\) 並執行它。  
  
2.  將 vsintr.exe 和 msdis150.dll 的路徑加入至系統路徑。  
  
    > [!NOTE]
    >  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的預設安裝中，vsinstr.exe 和 msdis150.dll 位於 \\Program Files\\Visual Studio 10\\Team Tools\\Performance Tools 中。  
  
3.  在命令提示字元中輸入 **VSInstr**。  
  
    > [!NOTE]
    >  如果畫面上顯示 vsinstr.exe 的用法資訊，表示您已正確設定所有項目。  如果出現錯誤，表示找不到 vsinstr.exe 或它的其中一個相依項目，請確定您已按照步驟 2 的說明，正確設定路徑。  
  
4.  將您的 **\_NT\_SYMBOL\_PATH** 變數設定為 **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols**，以設定符號伺服器  
  
5.  使用系統環境變數設定符號伺服器之後，在新的命令提示字元中執行命令列分析工具。  如此便可讓新的環境變數生效。  在命令提示字元視窗中輸入下列命令：  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  如需如何設定符號伺服器套件的詳細說明，請參閱 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)。  
  
6.  使用 [VSPerfReport](../profiling/vsperfreport.md) 工具將符號序列化到程式碼剖析資料 \(.vsp\) 檔中。  使用 **VSPerfReport \/summary:all \/packsymbols** 參數。  如果沒有符號要插入資料檔中，請確定您是否已設定 \_NT\_SYMBOL\_PATH 環境變數。  
  
## 請參閱  
 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [逐步解說：使用取樣進行命令列剖析](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)   
 [逐步解說：使用檢測進行命令列剖析](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)