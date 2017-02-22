---
title: "如何：使用命令列將程式碼剖析工具附加至 ASP.NET Web 應用程式以收集並行資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令列將程式碼剖析工具附加至 ASP.NET Web 應用程式以收集並行資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何利用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具，將分析工具附加至 ASP.NET 應用程式，以及收集處理序和執行緒並行資料。  
  
 程式碼剖析工具的命令列工具位於Visual Studio安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上皆可使用64 位元和 32 位元版本的工具。  若要在命令提示字元中使用程式碼剖析工具，必須將工具路徑加至 \[**命令提示字元**\] 視窗的 PATH 環境變數，或加至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 為了收集並行資料，將分析工具附加至裝載網站的 ASP.NET 背景工作處理序。  在程式碼剖析工具附加至應用程式的過程中，您可以暫停並繼續資料收集。  若要結束程式碼剖析工作階段，程式碼剖析工具必須不再附加於應用程式，而且程式碼剖析工具必須明確關閉。  在大部分情況下，您應在工作階段結束時清除程式碼剖析環境變數。  
  
## 附加程式碼剖析工具  
  
#### 若要將程式碼剖析工具附加至 ASP.NET 應用程式  
  
1.  輸入下列命令啟動程式碼剖析工具：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency \/output:**`OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) 選項會初始化分析工具以收集資源爭用資料。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     您可以使用下表中的任何選項搭配 **\/start**  選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|指定得到授權存取程式碼剖析工具之帳戶的選擇性網域以及使用者名稱。|  
    |[\/crosssession](../profiling/crosssession.md)|在其他登入工作階段的處理序中啟用程式碼剖析。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設值為 500。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
2.  以一般方式啟動 ASP.NET 應用程式。  
  
3.  透過輸入下列命令的方式，將程式碼剖析工具附加至 ASP.NET 背景工作處理序：**VSPerfCmd \/attach:**`PID` \[**\/targetclr:**`Version`\]  
  
    -   `PID` 會指定 ASP.NET 背景工作處理序的 ID 或名稱。  您可以在 \[Windows 工作管理員\] 中檢視所有執行中處理序的處理序 ID。  
  
    -   如果有多個 Common Language Runtime \(CLR\) 版本載入到應用程式中，則 [\/targetclr](../profiling/targetclr.md)**:**`Version` 會指定要進行程式碼剖析的 Runtime 版本。  這個參數是一個選擇性項目。  
  
## 控制資料收集  
 當應用程式正在執行時，您可以使用 VSPerfCmd.exe 選項，藉由啟動或停止寫入資料於檔案中，來控制資料收集情況。  您可以透過資料收集的控制來收集程式執行中特定時間的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下表中的 VSPerfCmd 選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|針對處理序 ID \(`PID`\) 所指定的處理序，啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 資料收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 會開始針對處理序 ID \(`PID`\) 或處理序名稱 \(*ProcName*\) 指定的處理序來收集資料。  **\/detach** 會停止對指定的處理序收集資料，如果沒有指定處理序，則停止所有處理序的資料收集。|  
  
## 結束程式碼剖析工作階段  
 要結束程式碼剖析工作階段時，程式碼剖析工具必須停止收集資料。  您可以藉由重新啟動 ASP.NET 背景工作處理序或啟用 **VSPerfCmd \/detach** 選項，來停止收集來自於使用並行方法進行程式碼剖析的應用程式中的資料。  接著啟用 **VSPerfCmd \/shutdown** 選項，關閉程式碼剖析工具並關閉程式碼剖析資料檔案。  **VSPerfClrEnv \/globaloff** 命令會清除程式碼剖析環境變數，但是系統組態在電腦重新啟動後才會重設。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  藉由關閉程式碼剖析工具或在命令提示字元中輸入下列命令的方式，來中斷程式碼剖析工具與目標應用程式之間的連結：  
  
     **VSPerfCmd \/detach**  
  
2.  在命令提示字元上輸入下列命令來關閉程式碼剖析工具：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## 請參閱  
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [使用 VSPerfASPNETCmd 快速進行網站程式碼剖析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)