---
title: "使用 VSPerfASPNETCmd 快速進行網站程式碼剖析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼剖析工具，VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 使用 VSPerfASPNETCmd 快速進行網站程式碼剖析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**VSPerfASPNETCmd** 命令列工具可讓您對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式輕鬆進行程式碼剖析。  相較於 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具，選項減少、不必設定環境變數，也不需要重新啟動電腦。  使用 **VSPerfASPNETCmd** 是以獨立分析工具進行程式碼剖析的慣用方法。  如需詳細資訊，請參閱[如何：安裝獨立分析工具](../profiling/how-to-install-the-stand-alone-profiler.md)。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 在某些案例中，例如收集並行資料或暫停程式碼剖析後再繼續，使用 **VSPerfCmd** 是慣用的程式碼剖析方法。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，請使用位於 32 位元 \\Team Tools\\Performance Tools 目錄中的 VSPerfASPNETCmd 工具。  若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
## 對 ASP.NET 應用程式進行程式碼剖析  
 若要對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式進行程式碼剖析，請輸入下列各節所描述的命令。  網站隨即啟動，而且分析工具會開始收集資料。  執行應用程式，然後關閉瀏覽器。  若要停止程式碼剖析，請在命令提示字元視窗中按下 ENTER 鍵。  
  
> [!NOTE]
>  根據預設，在 **vsperfaspnetcmd** 命令後不會傳回命令提示字元。  您可以使用 **\/nowait** 選項來強制傳回命令提示字元。  請參閱 [使用 /NoWait 選項](#UsingNoWait)  
  
## 若要使用取樣方法收集應用程式統計資料  
 取樣是 **VSPerfASPNETCmd** 工具的預設程式碼剖析方法，不必在命令列上設定。  下列命令列會從指定的 Web 應用程式收集應用程式統計資料：  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## 若要使用檢測方法收集詳細的計時資料  
 使用下列命令列，從動態編譯的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式收集詳細計時資料：  
  
 **vsperfaspnetcmd \/trace**  *websiteUrl*  
  
 如果您想要為 Web 應用程式中靜態編譯的.dll 檔案進行程式碼剖析，則必須使用 [VSInstr](../profiling/vsinstr.md) 命令列工具檢測檔案。  vsperfaspnetcmd \/trace 命令會包含來自受檢測檔案的資料。  
  
## 若要收集 .NET 記憶體資料  
 **\/Memory** 選項會收集 .NET 記憶體中的物件配置相關資料，也可以收集這些物件存留期的相關資訊。  配置資料收集是 **\/Memory** 資料選項的預設模式，不必在命令列上設定。  
  
 **vsperfaspnetcmd \/memory** *websiteUrl*  
  
 使用 **Lifetime** 參數，除了配置資料之外，還會收集物件存留期資料：  
  
 **vsperfaspnetcmd \/memory:lifetime** *websiteUrl*  
  
 您也可以使用 **\/Trace** 選項，將詳細的計時資料包含在 .NET 記憶體資料中：  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/trace** `websiteUrl`  
  
## 若要收集階層互動資料  
  
> [!WARNING]
>  使用 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 或 [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]，階層互動分析資料 \(TIP\) 可以被收集。  不過，階層互動分析資料只能在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 和 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 中檢視。  
>   
>  若要在 Windows 8 或 Windows Server 2012 的 TIP 資料，您必須使用檢測 \(**\/trace**\) 選項。  
  
 若要收集階層互動資料與取樣資料：  
  
 **vsperfaspnetcmd \/tip** `websiteUrl`  
  
 若要收集階層互動資料與檢測資料：  
  
 **vsperfaspnetcmd \/trace \/tip** *websiteUrl*  
  
 若要收集階層互動資料與 .NET 記憶體資料：  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/tip** *websiteUrl*  
  
##  <a name="UsingNoWait"></a> 使用 \/NoWait 選項  
 根據預設，在 **vsperfaspnetcmd** 命令後不會傳回命令提示字元。  您可以使用下列語法選項來強制傳回命令提示字元。  然後，您可以在命令提示字元視窗中執行其他作業。  若要結束程式碼剖析，請在個別的 **vsperfaspnetcmd** 命令中使用 **\/shutdown** 選項。  
  
 若要開始程式碼剖析：  
  
 **vsperfaspnetcmd** \[*\/Options*\] **\/nowait** *websiteUrl*  
  
 若要結束程式碼剖析：  
  
 **vsperfaspnetcmd \/shutdown** *websiteUrl*  
  
## 其他選項  
 您可以將下列任何選項加入至本節上列的命令，但 **vsperfaspnetcmd \/shutdown** 命令除外。  
  
|選項|說明|  
|--------|--------|  
|**\/Output:** `VspFile`|根據預設，程式碼剖析資料 \(.vsp\) 檔案是在目前目錄中以檔案名稱 **PerformanceReport.vsp** 建立的。  使用 \/output 選項指定不同的位置、檔案名稱或兩者。|  
|**\/PackSymbols:Off**|根據預設，VsPerfASPNETCmd 會將符號 \(函式、參數名稱等等\) 內嵌於 .vsp 檔案。  符號內嵌會讓程式碼剖析資料檔案變得非常大。  如果您在分析資料時仍然可以存取包含符號的 .pdb 檔案，請使用 \/packsymbols:off 選項停用符號內嵌。|