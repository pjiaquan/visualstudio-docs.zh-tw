---
title: "如何：使用命令列將程式碼剖析工具附加至 .NET Framework 獨立應用程式以收集記憶體資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令列將程式碼剖析工具附加至 .NET Framework 獨立應用程式以收集記憶體資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 程式碼剖析工具命令列工具將分析工具附加至執行中的 .NET Framework 獨立 \(用戶端\) 應用程式，以及收集記憶體資料。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用分析工具命令列工具，您必須將工具路徑加入至 \[命令提示字元\] 視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要附加至 .NET Framework 應用程式並收集記憶體資料，您必須在目標應用程式啟動之前，使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化適當的環境變數。  當程式碼剖析工具附加至應用程式時，您可以使用 **VSPerfCmd.exe** 工具暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，程式碼剖析工具必須從所有已進行程式碼剖析的處理序中斷連結，而且程式碼剖析工具必須明確地關閉。  在許多情況下，我們建議在工作階段結尾清除程式碼剖析環境變數。  
  
## 附加程式碼剖析工具  
  
#### 若要將程式碼剖析工具附加至執行中的 .NET Framework 應用程式  
  
1.  開啟 \[命令提示字元\] 視窗。  
  
2.  初始化程式碼剖析環境變數。  型別：  
  
     **VSPerfClrEnv** {**\/samplegc** &#124; **\/samplegclife**} \[**\/samplelineoff**\]  
  
    -   **\/samplegc** 和 **\/samplegclife** 選項會指定是否只收集記憶體配置資料，或收集記憶體配置和物件存留期資料。  只能指定一個選項。  
  
        |選項|說明|  
        |--------|--------|  
        |**\/samplegc**|僅收集記憶體配置資料。|  
        |**\/samplegclife**|同時收集記憶體配置和物件留存期資料。|  
  
    -   **\/samplelineoff** 選項會停用原始程式碼行號資料的收集功能。  
  
3.  啟動程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:sample** 選項會初始化程式碼剖析工具。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     下列任何選項都可以搭配 **\/start:sample** 選項使用。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有已進行程式碼剖析處理序之帳戶的網域和使用者名稱。  只有在處理序是以非登入使用者的身分執行時，才需要這個選項。  處理序擁有人列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。|  
    |[\/crosssession &#124; \/cs](../profiling/crosssession.md)|對其他工作階段中的處理序啟用程式碼剖析。  如果應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段識別項列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段識別碼\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
  
4.  如果有必要，請以一般方式啟動目標應用程式。  
  
5.  將程式碼剖析工具附加到目標應用程式。  型別：  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` 指定目標應用程式的處理序 ID。  `ProcessName` 會指定處理序的名稱。  請注意，如果指定 `ProcessName`，而同時有多個相同名稱的處理序正在執行，則結果無法預期。  您可以在 \[Windows 工作管理員\] 中檢視所有執行中處理序的處理序 ID。  
  
    -   如果有多個 Common Language Runtime \(CLR\) 版本載入到某一種應用程式中，則 **\/targetclr:**`Version` 會指定要進行程式碼剖析的 Runtime 版本。  選擇項。  
  
## 控制資料收集  
 當目標應用程式正在執行時，您可以使用 **VSPerfCmd.exe** 選項啟動及停止將資料寫入檔案，以控制資料收集。  資料收集控制可讓您收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下列選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對 `PID` 所指定的處理序進行資料收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 會開始針對 `PID` 或處理序名稱 \(ProcName\) 指定的處理序收集資料。  **\/detach** 會停止對指定的處理序收集資料，如果沒有指定特定的處理序，則停止所有處理序的資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，程式碼剖析工具必須從所有已進行程式碼剖析的處理序中斷連結，而且程式碼剖析工具必須明確地關閉。  您可以藉由關閉應用程式或呼叫 **VSPerfCmd \/detach** 選項，從已使用取樣方法進行程式碼剖析的應用程式中斷連結分析工具。  接著呼叫 **VSPerfCmd \/shutdown** 選項，關閉分析工具並關閉程式碼剖析資料檔案。  **VSPerfClrEnv \/off** 命令會清除程式碼剖析環境變數。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  請執行下列其中一個步驟，從目標應用程式中斷連結程式碼剖析工具：  
  
    -   輸入 **VSPerfCmd \/detach**  
  
         \-或\-  
  
    -   關閉目標應用程式。  
  
2.  關閉程式碼剖析工具。  型別：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
3.  \(選擇項\) 清除程式碼剖析環境變數。  型別：  
  
     **VSPerfCmd \/off**  
  
## 請參閱  
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)