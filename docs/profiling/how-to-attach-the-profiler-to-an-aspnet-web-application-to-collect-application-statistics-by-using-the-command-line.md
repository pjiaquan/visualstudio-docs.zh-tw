---
title: "如何：使用命令列將程式碼剖析工具附加至 ASP.NET Web 應用程式以收集應用程式統計資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令列將程式碼剖析工具附加至 ASP.NET Web 應用程式以收集應用程式統計資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具將分析工具附加至 ASP.NET Web 應用程式，以及使用取樣方法收集效能統計資料。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
>   
>  有命令列程式碼剖析工具的特定程序才可將階層互動資料加入至程式碼剖析。  請參閱 [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。  
>   
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用分析工具命令列工具，您必須將工具路徑加入至 \[命令提示字元\] 視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要收集 ASP.NET Web 應用程式的效能資料，則必須初始化適當的環境變數，並重新啟動裝載 ASP.NET Web 應用程式的電腦，以設定 Web 伺服器進行程式碼剖析。  
  
 接著將程式碼剖析工具附加至裝載網站的 ASP.NET 背景工作處理序。  當程式碼剖析工具附加至應用程式時，您可以暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，程式碼剖析工具必須從已進行程式碼剖析的應用程式中斷連結，而且程式碼剖析工具必須明確關閉。  在許多情況下，我們建議在工作階段結尾清除程式碼剖析環境變數。  
  
## 啟動程式碼剖析工具並附加至 ASP.NET Web 應用程式  
  
#### 若要將程式碼剖析工具附加至 ASP.NET Web 應用程式  
  
1.  開啟 \[命令提示字元\] 視窗。  
  
2.  初始化程式碼剖析環境變數。  型別：  
  
     **VSPerfClrEnv \/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** 啟用取樣。  
  
    -   **\/samplelineoff** 會停用將收集的資料指派到特定原始碼程式行。  已指定這個選項時，資料只會指派給函式。  
  
3.  重新啟動電腦。  
  
4.  啟動程式碼剖析工具。  輸入：**VSPerfCmd** [\/start](../profiling/start.md)**:sample** [\/output](../profiling/output.md)**:**`OutputFile`\[`Options`\]  
  
    -   **\/start:sample** 選項會初始化程式碼剖析工具。  
  
    -   **\/output:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     下列任何一個選項都可以搭配 **\/start:sample** 選項使用。  
  
    > [!NOTE]
    >  ASP.NET 應用程式通常需要 **\/user** 和 **\/crosssession** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有 ASP.NET 背景工作處理序之帳戶的網域和使用者名稱。  如果處理序是以非登入使用者的身分執行，就必須使用這個選項。  處理序擁有人列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他登入工作階段中的處理序啟用程式碼剖析。  如果 ASP.NET 應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段識別項列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段 ID\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
5.  以一般方式啟動 ASP.NET Web 應用程式。  
  
6.  將程式碼剖析工具附加至 ASP.NET 背景工作處理序。  輸入：**VSPerfCmd** [\/attach](../profiling/attach.md)**:**{`PID` &#124;`ProcName`} \[`Sample Event`\] \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` 會指定 ASP.NET 背景工作處理序的處理序 ID；`ProcName` 會指定背景工作處理序的名稱。  您可以在 \[Windows 工作管理員\] 中檢視所有執行中處理序的處理序 ID 和名稱。  
  
    -   根據預設，效能資料為每 10,000,000 個未暫止處理器時脈循環取樣一次。  在 1GH 的處理器上，約每秒鐘 100 次。  您可以指定下列其中一個 **VSPerfCmd** 選項，變更時脈循環間隔或指定不同的取樣事件。  
  
    |取樣事件|描述|  
    |----------|--------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|將取樣間隔變更為 `Interval` 所指定的未暫止時脈循環數目。|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|將取樣事件變更為分頁錯誤。  如果已指定 `Interval`，則會設定樣本之間的分頁錯誤數目。  預設值為 10。|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[`:``Interval`\]|將取樣事件變更為從處理序對作業系統核心的系統呼叫 \(syscall\)。  如果已指定 `Interval`，則會設定樣本之間的呼叫數目。  預設值為 10。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|將取樣事件和間隔變更為 `Config` 中指定的處理器效能計數器和間隔。|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|如果有多個 Common Language Runtime \(CLR\) 版本載入到應用程式中，指定要進行程式碼剖析的 Runtime 版本。|  
  
    -   如果有多個 CLR 版本載入到應用程式中，則 **targetclr:**`Version` 會指定要進行程式碼剖析的 Runtime 版本。  選擇項。  
  
## 控制資料收集  
 當應用程式正在執行時，您可以使用 **VSPerfCmd.exe** 選項啟動及停止將資料寫入檔案，以控制資料收集。  資料收集控制可讓您收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下列 **VSPerfCmd** 選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` **\/processoff:**`PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對 `PID` 所指定的處理序進行資料收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 會開始針對 `PID` 或處理序名稱 \(ProcName\) 指定的處理序收集資料。  **\/detach** 會停止對指定的處理序收集資料，如果沒有指定特定的處理序，則停止所有處理序的資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，請關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式，然後使用 Internet Information Services \(IIS\) **IISReset** 命令關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。  呼叫 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 選項，關閉分析工具並關閉程式碼剖析資料檔案。  
  
 **VSPerfClrEnv \/globaloff** 命令會清除程式碼剖析環境變數。  您必須重新啟動電腦，才能套用新的環境設定。  
  
 **VSPerfClrEnv \/globaloff** 命令會清除程式碼剖析環境變數，但是系統組態在電腦重新啟動後才會重設。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  請執行下列其中一個動作，從目標應用程式中斷連結程式碼剖析工具：  
  
    -   輸入 **VSPerfCmd \/detach**  
  
         \-或\-  
  
    -   關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。  
  
2.  關閉程式碼剖析工具。  輸入：**VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
3.  \(選擇項\) 清除程式碼剖析環境變數。  型別：  
  
     **VSPerfCmd \/globaloff**  
  
4.  重新啟動電腦。  
  
## 請參閱  
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)