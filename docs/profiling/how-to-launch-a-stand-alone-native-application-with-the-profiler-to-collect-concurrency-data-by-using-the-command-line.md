---
title: "如何：使用命令列搭配程式碼剖析工具啟動獨立的原生應用程式以收集並行資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令列搭配程式碼剖析工具啟動獨立的原生應用程式以收集並行資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具啟動原生獨立 \(用戶端\) 應用程式，以及收集處理序和執行緒並行資料。  
  
 程式碼剖析工作階段包含下列部分：  
  
-   以程式碼剖析工具啟動應用程式  
  
-   控制資料收集  
  
-   結束程式碼剖析工作階段  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要在命令提示字元中使用程式碼剖析工具，必須將工具路徑加入至 \[**命令提示字元**\] 視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
## 以程式碼剖析工具啟動應用程式  
 若要使用程式碼剖析工具啟動目標應用程式，請使用 [VSPerfCmd.exe](../profiling/vsperfcmd.md) **\/start** 和 **\/launch**選項初始化程式碼剖析工具並啟動應用程式。  您可以指定 **\/start** 和 **\/launch** 及其個別選項。  您也可以加入 **\/globaloff** 選項，在目標應用程式啟動時暫停資料收集。  接著使用 **\/globalon** 開始收集資料。  
  
#### 若要以程式碼剖析工具啟動應用程式  
  
1.  在命令提示字元中輸入下列命令：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     [\/output](../profiling/output.md) **:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     您可以使用下表中的任何選項搭配 **\/start:concurrency** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設值為 500。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
2.  輸入下列內容以啟動目標應用程式：  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\]  
  
     您可以使用下表中的任何選項搭配 **\/launch** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|指定字串，其中包含要傳遞至目標應用程式的命令列引數。|  
    |[\/console](../profiling/console.md)|在另一個視窗中啟動目標命令列應用程式。|  
    |[\/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|如果應用程式載入多個 CLR 版本，則會指定要進行程式碼剖析的 Common Language Runtime \(CLR\) 版本。|  
  
## 控制資料收集  
 當目標應用程式正在執行時，您可以使用 VSPerfCmd.exe 選項啟動及停止將資料寫入檔案，以控制資料收集。  您可以透過資料收集的控制，收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下表中的選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|針對處理序 ID \(`PID`\) 所指定的處理序，啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 資料收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 會開始針對處理序 ID \(`PID`\) 或處理序名稱 \(*ProcName*\) 指定的處理序來收集資料。  **\/detach** 會停止對指定的處理序收集資料，如果沒有指定處理序，則停止所有處理序的資料收集。|  
  
-   您也可以使用 **VSPerfCmd.exe** [\/mark](../profiling/mark.md) 選項，將程式碼剖析標記插入資料檔案。  **\/mark** 命令會加入識別項、時間戳記和選擇性使用者定義的文字字串。  標記可用來篩選程式碼剖析工具報告和資料檢視中的資料。  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，程式碼剖析工具不能正在收集資料。  您可以藉由關閉程式碼剖析的應用程式或叫用 **VSPerfCmd \/detach** 選項，停止收集並行資料。  接著叫用 **VSPerfCmd \/shutdown** 選項，關閉程式碼剖析工具並關閉程式碼剖析資料檔案。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  透過關閉程式碼剖析工具或在命令提示字元中輸入下列命令的方式，中斷程式碼剖析工具與目標應用程式的連結：  
  
     **VSPerfCmd \/detach**  
  
2.  在命令提示字元上輸入下列命令，關閉程式碼剖析工具：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)