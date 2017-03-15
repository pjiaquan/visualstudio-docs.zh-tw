---
title: "啟動 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 啟動
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Launch** 選項會使用取樣方法來啟動程式碼剖析工具，也會啟動指定的應用程式。  
  
 若要使用 **Launch** 選項，您必須在 **Start** 選項中指定 **Sample** 方法。  
  
## 語法  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### 參數  
 `AppName`  
 要啟動的應用程式名稱。  支援目前目錄中的完整和部分路徑。  
  
## 有效的選項  
 下列 VSPerfCmd 選項可以在單一命令列中搭配 **Launch** 選項使用。  
  
 **Start:** `Method`  
 初始化命令列程式碼剖析工具工作階段，並設定指定的程式碼剖析方法。  
  
 **GlobalOn**和 **GlobalOff**  
 繼續 \(**GlobalOn**\) 或暫停 \(**GlobalOff**\) 程式碼剖析，但是不會結束程式碼剖析工作階段。  
  
 **ProcessOn:** `PID` 和 **ProcessOff**:`PID`  
 繼續 \(**ProcessOn**\) 或暫停 \(**ProcessOff**\) 指定之處理序的程式碼剖析。  
  
 **TargetCLR**  
 當有多個 .NET Framework Common Language Runtime \(CLR\) 版本載入到程式碼剖析工作階段時，指定要進行程式碼剖析的版本。  根據預設，會對第一個載入的版本進行程式碼剖析。  
  
## 專有選項  
 下列選項只能搭配 **Launch** 選項使用。  
  
 **Console**  
 在新的視窗中啟動指定的命令列應用程式。  
  
 **Args:** `ArgList`  
 指定要傳遞給應用程式之引數的清單。  
  
 **LineOff**  
 停用程式行層級之程式碼剖析資料的收集。  
  
## 取樣選項  
 下列其中一個取樣間隔選項可以在 **Launch** 命令列上指定。  預設的取樣間隔為 10,000,000 次處理器時脈週期。  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**`Events`\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]**GC**\[:**allocation**&#124;**lifetime**\]  
 指定取樣間隔的數目和類型。  
  
-   **Timer** \- 每隔 `Cycles` 未暫止的處理器時脈週期時取樣。  如果未指定 `Cycles`，則會使用 10,000,000 次週期。  
  
-   **PF** \- 每隔 `Events` 個分頁錯誤時取樣。  如果未指定 `Events`，則為 10 個分頁錯誤。  
  
-   **Sys** \- 每隔 `Events` 次呼叫作業系統時取樣。  如果未指定 `Events`，則會使用 10 次系統呼叫。  
  
-   **Counter** \- 每隔 `Name` 指定之 CPU 效能計數器 `Reload` 次時取樣。  或者，`FriendlyName` 可以指定一個字串，做為程式碼剖析工具報告的資料行標題。  
  
-   **GC** \- 收集 .NET 記憶體資料。  根據預設 \(**allocation**\)，資料會於每次記憶體配置事件收集。  已指定 **lifetime** 參數時，也會在每個記憶體回收事件時收集資料。  
  
## 範例  
 這個範例示範如何使用 **Launch** 來啟動應用程式。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)