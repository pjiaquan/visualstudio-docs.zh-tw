---
title: "PF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# PF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **PF** 選項會將取樣的程式碼剖析事件設定為分頁錯誤，並且選擇性地將取樣間隔從預設的 10 變更為分頁錯誤的次數。  
  
> [!NOTE]
>  64 位元的系統上不能使用 PF。  
  
 **注意事項** 64 位元電腦不支援 **PF**。**PF** 只能在同時包含 **Launch** 或 **Attach** 選項的命令列中使用。  
  
 根據預設，取樣事件會設定為未暫止的處理器時脈週期，且取樣間隔設定為 10,000,000。  **Timer**、**PF**、**Sys** 和 **Counter** 選項可讓您設定樣本事件和取樣間隔。  **GC** 選項會在每個配置和記憶體回收事件時收集 .NET 記憶體資料。  在命令列上只能指定這些選項的其中一個。  
  
 取樣事件和取樣間隔只能在包含 **Launch** 或 **Attach** 選項的第一個命令列中設定。  
  
## 語法  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### 參數  
 `Events`  
 指定取樣間隔中分頁錯誤事件數目的整數值。  如果未指定 `Events`，則間隔會設定為 10。  
  
## 必要選項  
 **PF** 只能在包含下列其中一個選項的命令列上指定。  
  
 **Launch:** `AppName`  
 啟動程式碼剖析工具以及 AppName 指定的應用程式。  
  
 **Attach:** `PID`  
 將程式碼剖析工具附加至 AppName 指定的處理序。  
  
## 無效的選項  
 下列選項無法在與 **PF** 相同的命令列上指定。  
  
 **Timer**\[**:**`Cycles`\]  
 將取樣事件設定為處理器時脈週期，並且選擇性地將取樣間隔設定為 `Cycles`。  預設 Timer 間隔為 10,000,000。  
  
 **Sys**\[**:**`Events`\]  
 將取樣事件設定為從程式碼剖析應用程式對作業系統核心的系統呼叫 \(syscall\)，並選擇性地將取樣間隔設定為 `Events`。  預設的 Sys 間隔為 10。  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 將取樣事件設定為 `Name` 所指定的 CPU 效能計數器，並將取樣間隔設定為 `Reload`。  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 收集 .NET 記憶體資料。  根據預設 \(**Allocation**\)，資料會於每次記憶體配置事件收集。  已指定 **Lifetime** 參數時，也會在每個記憶體回收事件時收集資料。  
  
## 範例  
 這個範例示範如何將程式碼剖析樣本事件設定為分頁錯誤，以及如何將取樣間隔設定為 20 個分頁錯誤。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)