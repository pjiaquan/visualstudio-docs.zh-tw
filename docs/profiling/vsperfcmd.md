---
title: "VSPerfCmd | Microsoft Docs"
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
  - "命令列, 工具"
  - "命令列工具, VSPerfCmd 工具"
  - "效能工具, VSPerfCmd 工具"
  - "程式碼剖析工具, VSPerfCmd"
  - "VSPerfCmd 工具"
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**VSPerfCmd.exe** 工具是用來啟動和停止效能資料收集作業。  這個工具使用下列語法：  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 下表說明 **VSPerfCmd.exe** 工具選項。  
  
|選項|說明|  
|--------|--------|  
|**U**|以 Unicode 格式撰寫已重新導向的主控台輸出。  必須是第一個指定的選項。|  
|[啟動](../profiling/start.md) **:** `mode`|以指定的模式啟動程式碼剖析服務。|  
|[輸出](../profiling/output.md) **:** `filename`|指定輸出檔名稱。  僅能與 **Start** 搭配使用。|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|啟用跨 Windows 工作階段程式碼剖析。  僅能與 **Start**、 **Attach**、 **or Launch** 搭配使用。|  
|[User](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|允許指定的帳戶存取程式碼剖析工具服務。  僅能與 **Start** 搭配使用。|  
|[WaitStart](../profiling/waitstart.md)\[**:**`n`\]|等待資料收集記錄器進行初始化。  如果指定 `n`，則 **VSPerfCmd** 最多會等待 `n` 秒。  如果未指定 `n`，則 **VSPerfCmd** 會一直等待。  這有助於使用 **VSPerfCmd** 做為批次處理的一部分。|  
|[計數器](../profiling/counter.md) **:** `cfg`|使用取樣程式碼剖析方法時，指定 CPU 計數器和要當做取樣間隔使用的事件數。  您只能針對一個計數器值取樣。<br /><br /> 使用檢測程式碼剖析方法時，指定要在每個檢測點收集的 CPU 計數器。  僅能與 **Start:**`Trace`、 **Attach**、或 **Launch** 搭配使用。|  
|[QueryCounters](../profiling/querycounters.md)|顯示目前電腦可用的 CPU 計數器清單。|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|指定要加入程式碼剖析標記資料的 Windows 效能計數器事件。  僅能與 **Start** 搭配使用。|  
|[AutoMark](../profiling/automark.md) **:** *n*|指定 Windows 效能計數器資料收集事件之間的時間間隔 \(以毫秒為單位\)。  與 **WinCounter** 一起使用。|  
|[事件](../profiling/events-vsperfcmd.md) **:** `option`|控制指定之 Windows 事件追蹤 \(ETW\) 事件的收集。  ETW 資料將收集至 .itl 檔案 \(不是程式碼剖析資料 \(.vsp\) 檔案\) 中。|  
|[Status](../profiling/status.md)|顯示程式碼剖析工具的狀態、目前正在進行程式碼剖析之處理序的相關資訊和具有程式碼剖析工具控制授權的帳戶。|  
|[關機](../profiling/shutdown.md)\[**:**`n`\]|關閉程式碼剖析資料檔案並關閉程式碼剖析工具。|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|在呼叫 **VSPerfCmd GlobalOff** 之後繼續收集資料。|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|停止所有資料收集，但不結束程式碼剖析工作階段。|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|在呼叫 **VSPerfCmd ProcessOff** 而暫停程式碼剖析之後繼續收集指定之處理序的資料。|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|停止指定之處理序的資料收集。|  
|[ThreadOn 和 ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|在呼叫 **VSPerfCmd ThreadOff** 而暫停程式碼剖析之後繼續指定之處理序的程式碼剖析。  請於使用檢測方法進行程式碼剖析時才使用 **ThreadOn**。|  
|[ThreadOn 和 ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|暫停指定之執行緒的程式碼剖析。  請於使用檢測方法進行程式碼剖析時才使用 **ThreadOff**。|  
|[標記](../profiling/mark.md) **:** *MarkNum*\[**,***MarkText***\]**|將標記插入程式碼剖析資料檔案 \(可包含選擇性的文字\)。|  
  
## 取樣方法選項  
 下列選項只有在您使用取樣程式碼剖析方法時才可使用。  
  
|選項|說明|  
|--------|--------|  
|[啟動](../profiling/launch.md) **:** *Executable*|啟動指定的應用程式並開始程式碼剖析。|  
|[Args](../profiling/args.md) **:** *Arguments*|指定命令列引數以傳遞給已啟動的應用程式。|  
|[主控台](../profiling/console.md)|以新的命令提示字元視窗啟動指定的命令。|  
|[附加](../profiling/attach.md) **:** *PID*\[**,***PID*\]|開始對指定的處理序執行程式碼剖析。  可以用處理序 ID 或處理序名稱來識別處理序。|  
|[中斷連結](../profiling/detach.md)\[**:***PID*\[,*PID*\]\]|停止對指定的處理序進行程式碼剖析。  可以用處理序 ID 或處理序名稱來識別處理序。  如果未指定處理序，所有處理序的程式碼剖析將暫止。|  
|[GC](../profiling/gc-vsperfcmd.md)\[**:**{**Allocation** `&#124;` **Lifetime**}\]|收集 .NET 記憶體配置和物件留存期資料。  僅能和 **VSPerfCmd Launch** 選項搭配使用。|  
  
### 取樣間隔選項  
 下列選項指定取樣間隔的類型和期間。  預設為 **Timer**。  您還可以使用 **Counter** 選項來指定 CPU 計數器當做間隔。  這些選項只能和 **Launch** 或程式碼剖析工作階段的第一個 **Attach** 一起指定。  
  
|選項|說明|  
|--------|--------|  
|[PF](../profiling/pf.md)\[**:***n*\]|在每 n 個分頁錯誤時取樣 \(n 預設值為 10\)。|  
|[Sys](../profiling/sys-vsperfcmd.md)\[**:***n*\]|在每 n 個系統呼叫時取樣 \(n 預設值為 10\)。|  
|[計時器](../profiling/timer.md)\[**:***n*\]|在每 n 個處理器循環時取樣 \(預設值\=10000000\)。|  
  
## 服務元件和核心模式裝置選項  
 下列 Admin 選項支援程式碼剖析服務元件或核心模式裝置驅動程式。  Admin 選項可設定程式碼剖析使用權限及控制已進行程式碼剖析的服務或裝置驅動程式。  
  
 Admin 選項必須在以系統管理認證執行的命令提示字元下執行。  
  
|選項|說明|  
|--------|--------|  
|**Admin:Security** \<**ALLOW&#124;DENY**\> *Right*\[ *Right*\] \<*User*&#124;*Group*\>|允許或拒絕指定的使用者或群組存取程式碼剖析服務。<br /><br /> `Right` 可以是：<br /><br /> CrossSession \- 賦予使用者存取服務的權限，以便進行跨工作階段程式碼剖析。<br /><br /> SampleProfiling \- 賦予使用者存取驅動程式的權限，以啟用取樣程式碼剖析。  也可以在追蹤程式碼剖析期間，用來存取核心轉換資訊。<br /><br /> FullAccess \- 賦予使用者存取 CrossSession 和 SampleProfiling 的權限。|  
|**Admin:Security, List**|列出程式碼剖析服務目前的狀態，並列出使用者權限。|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**\>|啟動、停止、安裝或解除安裝程式碼剖析服務元件 \(Service\) 或核心模式裝置驅動程式 \(Driver\)。|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>**AutoStart** `` \<**ON**&#124;**OFF**\>|啟用或停用在重新開機後自動啟動程式碼剖析服務 \(Service\) 或核心模式裝置驅動程式 \(Driver\) 的功能。|  
  
## VSPerfCmd \/Driver  
 **VSPerfCmd \/Driver** 選項目前已過時。  如需此功能，請使用 **VsPerfCmd Admin** 選項。  
  
## 請參閱  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)