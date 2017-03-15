---
title: "如何：使用命令列以程式碼剖析工具啟動獨立的 .NET Framework 應用程式並收集並行資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令列以程式碼剖析工具啟動獨立的 .NET Framework 應用程式並收集並行資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具啟動 .NET Framework 獨立 \(用戶端\) 應用程式，以及收集處理序和執行緒並行資料。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 當程式碼剖析工具附加至應用程式時，您可以暫停和繼續資料收集。  若要結束程式碼剖析工作階段，程式碼剖析工具必須不再附加至應用程式，而且程式碼剖析工具必須明確關閉。  
  
## 以程式碼剖析工具啟動應用程式  
 若要使用程式碼剖析工具啟動 .NET Framework 目標應用程式，可以使用 VSPerfClrEnv.exe 設定 .NET Framework 程式碼剖析變數。  然後使用 VSPerfCmd **\/start** 和 **\/launch** 選項初始化程式碼剖析工具並啟動應用程式。  在單一命令列上，可指定 **\/start** 和 **\/launch** 以及其個別選項。  您也可以將 **\/globaloff** 選項加入至命令列，以在目標應用程式啟動時暫停資料收集。  然後在另一個命令列上使用 **\/globalon** 開始收集資料。  
  
#### 若要以程式碼剖析工具啟動應用程式  
  
1.  開啟命令提示字元視窗。  
  
2.  啟動程式碼剖析工具。  型別：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency**\[**,**{**ResourceOnly**&#124;**ThreadOnly**}\] **\/output:**`OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) 選項會初始化此分析工具。  
  
        |||  
        |-|-|  
        |**\/start:concurrency**|啟用收集資源爭用和執行緒執行資料。|  
        |**\/start:concurrency,resourceonly**|只啟用收集資源爭用資料。|  
        |**\/start:concurrency,threadonly**|只啟用收集執行緒執行資料。|  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     下列任何選項都可以搭配 **\/start:concurrency** 選項使用。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|指定將被授權存取程式碼剖析工具之帳戶的選擇性網域和使用者名稱。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他登入工作階段中的處理序啟用程式碼剖析。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
3.  啟動目標應用程式。  型別：  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\] \[`Sample Event`\]  
  
     下列任何選項都可以搭配 **\/launch** 選項使用。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|指定字串，其中包含要傳遞至目標應用程式的命令列引數。|  
    |[\/console](../profiling/console.md)|在另一個視窗中啟動目標命令列應用程式。|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|如果有多個 Common Language Runtime \(CLR\) 版本載入到應用程式中，指定要進行程式碼剖析的 Runtime 版本。|  
  
## 控制資料收集  
 當目標應用程式正在執行時，您可以使用 VSPerfCmd.exe 選項，啟動及停止將資料寫入檔案，以控制資料收集。  資料收集控制可讓您收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
1.  下面的 VSPerfCmd.exe 選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對處理序 ID \(`PID`\) 所指定的處理序進行資料收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 會開始針對處理序 ID \(`PID`\) 或處理序名稱 \(ProcName\) 指定的處理序來收集資料。  **\/detach** 會停止對指定的處理序收集資料，如果沒有指定特定的處理序，則停止所有處理序的資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，程式碼剖析工具不能正在收集資料。  您可以藉由關閉程式碼剖析的應用程式或叫用 **VSPerfCmd \/detach** 選項，停止收集並行資料。  接著叫用 **VSPerfCmd \/shutdown** 選項，關閉程式碼剖析工具並關閉程式碼剖析資料檔案。  **VSPerfClrEnv \/off** 命令會清除程式碼剖析環境變數。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  請執行下列其中一個動作，從目標應用程式中斷連結程式碼剖析工具。  
  
    -   關閉目標應用程式。  
  
         \-或\-  
  
    -   輸入 **VSPerfCmd \/detach**  
  
2.  關閉程式碼剖析工具  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## 請參閱  
 [收集並行資料](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)