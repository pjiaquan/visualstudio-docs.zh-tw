---
title: "ProcessOn 和 ProcessOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ProcessOn 和 ProcessOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **ProcessOff** 及 **ProcessOn** 子命令會暫停和繼續對命令列程式碼剖析工作階段中指定的處理序進行的程式碼剖析。  **ProcessOff** 會停止對處理序進行程式碼剖析，**ProcessOn** 則會開始對處理序進行程式碼剖析。  
  
 在大部分的情況下，您會指定 **ProcessOn** 或 **ProcessOff** 做為 VSPerfCmd.exe 命令列中唯一的選項，但是它們也可以與 **GlobalOn**、**GlobalOff**、**ThreadOn** 以及 **ThreadOff** 子命令結合。  
  
 **ProcessOn** 和 **ProcessOff** 子命令會與控制命令列程式碼剖析工作階段中所有處理序之資料收集的 **GlobalOn** 和 **GlobalOff** 子命令互動，也會與控制指定之執行緒的資料收集的 **ThreadOn** 和 **ThreadOff** 子命令互動。  
  
 **ProcessOff** 和 **ProcessOn** 子命令也會影響程式碼剖析工具 API 函式操作的 \[處理序 Start\/Stop 計數\]。  
  
-   **ProcessOff** 會立即將 \[處理序 Start\/Stop 計數\] 設定為 0，因此會暫停程式碼剖析。  
  
-   **ProcessOn** 會立即將 \[處理序 Start\/Stop 計數\] 設定為 1，因此會繼續程式碼剖析。  
  
 如需詳細資訊，請參閱[程式碼剖析工具 API](../profiling/profiling-tools-apis.md)。  
  
## 語法  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### 參數  
 `PID`  
 要開始或停止之處理序的整數識別項。  處理序 ID 列於 Windows \[工作管理員\] 的 \[處理程序\] 索引標籤上。  
  
## 所需的子命令  
 None  
  
## 有效的子命令  
 **ProcessOn** 和 **ProcessOff** 可以在同時包含下列子命令的命令列上指定。  
  
 **Start:** `Method`  
 初始化命令列程式碼剖析工作階段，並設定指定的程式碼剖析方法。  
  
 **Launch:** `AppName`  
 啟動指定的應用程式並以取樣方法開始執行程式碼剖析。  
  
 **Attach:** `PID`  
 開始對指定的處理序進行程式碼剖析。  
  
 **GlobalOff**&#124;**GlobalOn**  
 停止或開始對命令列程式碼剖析工作階段中的所有處理序進行程式碼剖析。  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 停止或開始對指定的執行緒進行程式碼剖析 \(僅限檢測方法\)。  
  
## 範例  
 這個範例會使用 **ProcessOff** 子命令，以收集應用程式啟動的程式碼剖析資料。  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)