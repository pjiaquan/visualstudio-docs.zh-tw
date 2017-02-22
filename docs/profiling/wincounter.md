---
title: "WinCounter | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# WinCounter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**WinCounter** 選項會指定 Windows 或應用程式效能計數器，在執行程式碼分析期間以設定的間隔進行收集。  程式碼剖析資料檔案中會標記列出 Windows 及應用程式效能計數器。  您可以在個別選項中指定多個要收集的效能計數器。  
  
 根據預設，計數器會每隔 500 毫秒收集一次。  使用 **AutoMark** 選項可以指定不同的收集間隔。  
  
 只會使用一個 **AutoMark** 選項。  如果指定多個 **AutoMark** 選項，則會使用最後一個。  
  
 **WinCounter** 選項只能與 **Start** 選項搭配使用。  
  
## 語法  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### 參數  
 `Path`  
 採用 PDH 計數器路徑格式的 Windows 效能計數器。  
  
## 必要選項  
 **WinCounter** 選項只能與 **Start** 選項搭配使用。  
  
 **Start:** `Method`  
 **Start** 選項會將程式碼剖析工具初始化成指定的程式碼剖析方法。  
  
## 專有選項  
 **AutoMark** 選項只能與 **WinCounter** 選項搭配使用。  
  
 **AutoMark:** `Milliseconds`  
 指定 Windows 效能計數器資料收集之間的毫秒數。  
  
## 範例  
 在下列範例中，會指定兩個 Windows 效能計數器以 1000 毫秒的間隔進行收集。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)