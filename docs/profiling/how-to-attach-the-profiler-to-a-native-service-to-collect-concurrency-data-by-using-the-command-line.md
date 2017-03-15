---
title: "如何：使用命令列將程式碼剖析工具附加至原生服務以收集並行資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令列將程式碼剖析工具附加至原生服務以收集並行資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具將分析工具附加至原生 \(C\/C\+\+\) 服務，以及使用取樣方法收集處理序和執行緒並行資料。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於Visual Studio安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要在命令提示字元中使用程式碼剖析工具，必須將工具路徑加入至 \[**命令提示字元**\] 視窗的 PATH 環境變數，或加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 當程式碼剖析工具附加至服務時，您可以暫停和繼續資料收集。  若要結束程式碼剖析工作階段，程式碼剖析工具必須不再附加至服務，而且程式碼剖析工具必須明確地關閉。  
  
## 附加程式碼剖析工具  
 若要將程式碼剖析工具附加至原生服務，請使用 **VSPerfCmd \/start** 和 **\/attach** 選項初始化程式碼剖析工具，並將它附加至目標應用程式。  在單一命令列上，可指定 **\/start** 和 **\/attach** 以及其個別選項。  您也可以加入 **\/globaloff** 選項，在目標應用程式啟動時暫停資料收集。  接著使用 **\/globalon** 開始收集資料。  
  
#### 若要將程式碼剖析工具附加至原生服務  
  
1.  如果服務沒有執行，請啟動服務。  
  
2.  在命令提示字元中輸入下列命令，以啟動程式碼剖析工具：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     您可以使用下表中的任何選項搭配 **\/start**  選項。  
  
    > [!NOTE]
    >  大部分服務都需要 **\/user** 和 **\/crosssession** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|指定將被授權存取程式碼剖析工具之帳戶的選擇性網域和使用者名稱。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他登入工作階段中的處理序啟用程式碼剖析。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設值為 500。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
3.  在命令提示字元中輸入下列命令，將程式碼剖析工具附加至服務：  
  
     **VSPerfCmd \/attach:** `PID`  
  
     `PID` 指定目標應用程式的處理序 ID 或處理序名稱。  您可以在 \[Windows 工作管理員\] 中檢視所有執行中處理序的處理序 ID。  
  
## 控制資料收集  
 當目標應用程式正在執行時，您可以使用 VSPerfCmd.exe 選項啟動及停止將資料寫入檔案，以控制資料收集。  您可以透過資料收集的控制，收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下表中的選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|針對處理序 ID \(`PID`\) 所指定的處理序，啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 資料收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 會開始針對處理序 ID \(`PID`\) 或處理序名稱 \(*ProcName*\) 指定的處理序來收集資料。  **\/detach** 會停止對指定的處理序收集資料，如果沒有指定處理序，則停止所有處理序的資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，程式碼剖析工具不能正在收集資料。  您可以藉由停止服務或叫用 **VSPerfCmd \/detach** 選項，停止從使用並行方法進行程式碼剖析的原生服務中收集資料。  接著叫用 **VSPerfCmd \/shutdown** 選項，關閉程式碼剖析工具並關閉程式碼剖析資料檔案。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  透過停止服務或在命令提示字元中輸入下列命令的方式，中斷程式碼剖析工具與目標應用程式的連結：  
  
     輸入 **VSPerfCmd \/detach**  
  
2.  在命令提示字元上輸入下列命令，關閉程式碼剖析工具：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)