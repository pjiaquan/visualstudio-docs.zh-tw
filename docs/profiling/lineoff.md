---
title: "LineOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# LineOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根據預設，當您使用取樣程式碼剖析方法時，程式碼剖析工具會收集原始程式碼行號和行號位移資料。  如果 VSPerfCmd 用來啟動應用程式，則 VSPerfCmd **LineOff** 選項會停用行號資料收集。  當指定 **LineOff** 時，程式碼剖析資料會收集至函式層級。  
  
 您只能將 **LineOff** 與 **Launch** 選項搭配使用，而且只有在程式碼剖析工具已初始化為使用 **Start**:**Sample** 選項取樣時才能使用。  
  
## 語法  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### 參數  
 None  
  
## 必要選項  
 **LineOff** 選項只能在包含 **Launch** 選項的命令列上使用。  
  
 **Launch:** `AppName`  
 啟動指定的應用程式並以取樣方法開始執行程式碼剖析。  
  
## 範例  
 這個範例會啟動應用程式和程式碼剖析工具，並且停用程式行層級的取樣。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)