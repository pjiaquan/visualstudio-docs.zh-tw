---
title: "ThreadOn 和 ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ThreadOn 和 ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **ThreadOff** 和 **ThreadOn** 子命令都只能在使用檢測方法的命令列程式碼剖析工作階段中使用。  **ThreadOff** 和 **ThreadOn** 會讓指定的執行緒暫停和繼續程式碼剖析。  **ThreadOff** 會停止程式碼剖析執行緒，**ThreadOn** 則會開始程式碼剖析執行緒。  
  
 在大部分的情況下，您會指定 **ThreadOn** 或 **ThreadOff** 做為 VSPerfCmd.exe 命令列中唯一的選項，但是它們也可以與 **GlobalOn**、**GlobalOff**、**ProcessOn** 以及 **ProcessOff** 子命令結合。  
  
 **ThreadOn** 和 **ThreadOff** 子命令會與控制命令列程式碼剖析工作階段中所有處理序之資料收集的 **GlobalOn** 和 **GlobalOff** 子命令互動，也會與控制指定之處理序的資料收集的 **ProcessOn** 和 **ProcessOff** 子命令互動。  
  
 **ThreadOff** 和 **ThreadOn** 子命令也會影響程式碼剖析工具 API 函式操作的 \[執行緒 Start\/Stop 計數\]。  
  
-   **ThreadOff** 會立即將 \[執行緒 Start\/Stop 計數\] 設定為 0，因此會暫停程式碼剖析。  
  
-   **ThreadOn** 會立即將 \[執行緒 Start\/Stop 計數\] 設定為 1，因此會繼續程式碼剖析。  
  
 如需詳細資訊，請參閱[程式碼剖析工具 API](../profiling/profiling-tools-apis.md)。  
  
## 語法  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### 參數  
 `TID`  
 要開始或停止之執行緒的整數識別項。  
  
## 有效的選項  
 **ThreadOn** 和 **ThreadOff** 可以在同時包含下列子命令的命令列上指定。  
  
 **Start:** `Method`  
 初始化命令列程式碼剖析工作階段，並設定指定的程式碼剖析方法。  
  
 **GlobalOff**&#124;**GlobalOn**  
 停止或開始對命令列程式碼剖析工作階段中的所有處理序進行程式碼剖析。  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 停止或開始對指定的處理序進行程式碼剖析。  
  
## 範例  
 這個範例會使用 **ThreadOff** 子命令停止收集程式碼剖析資料，以便只收集應用程式啟動資料。  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)