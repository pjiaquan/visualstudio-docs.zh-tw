---
title: "Args | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Args
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Args** 選項會指定傳遞至 **Launch** 子命令之目標應用程式的引數清單。  
  
 當命令列上也指定 **Launch** 時，才能指定 **Args**。  當指定 **Launch** 時，**Args** 便會是選擇項。  
  
## 語法  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### 參數  
 `Arguments`  
 **Launch** 命令之目標應用程式的引數清單。  
  
## 必要選項  
 **Launch:** `AppName`  
 啟動指定的應用程式並以取樣方法開始執行程式碼剖析。  
  
## 範例  
 下列範例使用 **Args** 選項將引數傳遞至 TestApp.exe。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)