---
title: "AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**AutoMark** 選項指定 Windows 軟體效能計數器事件集合之間的毫秒數。  Windows 效能計數器指定於 **WinCounter** 選項中。  
  
 命令列上只能指定一個 **AutoMark** 選項。  請注意，**AutoMark** 所指定的 **WinCounter** 取樣間隔與主要取樣間隔無關。  
  
## 語法  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### 參數  
 `Milliseconds`  
 指定 Windows 效能計數器事件集合之間的毫秒數。  
  
## 必要選項  
 **WinCounter:** `Path`  
 指定要收集的 Windows 效能計數器。  當您使用檢測方法時，可以指定多個 Windows 計數器。  當您使用取樣方法時，只能指定一個軟體計數器。  **WinCounter** 選項必須指定於命令列，且包含 **Start** 選項。  
  
## 範例  
 在這個範例中，會將兩個 Windows 效能計數器的取樣間隔設定為 1000 毫秒。  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)