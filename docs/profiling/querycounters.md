---
title: "QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**QueryCounters** 選項會列出電腦上可用的 CPU \(硬體\) 效能計數器。  
  
 **QueryCounters** 必須是命令列上的唯一選項。  
  
## 語法  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### 參數  
 None  
  
## 備註  
 當您使用檢測方法時，程式碼剖析工具可以在每個資料收集事件中，收集一個或多個 CPU 效能計數器的值。  當您使用取樣程式碼剖析方法時，可以指定一個計數器事件，以及要當做取樣間隔使用的事件發生次數。  
  
 不同的處理器會有不同的 CPU 效能計數器。  程式碼剖析工具會定義一組泛型計數器，可在幾乎所有處理器上使用。  **QueryCounters** 選項會同時列出泛型計數器的名稱和處理器專用計數器的名稱。  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)