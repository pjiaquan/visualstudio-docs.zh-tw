---
title: "主控台 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 主控台
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Console** 選項會在新的命令提示字元視窗中啟動指定的應用程式。  **Console** 只能與 VSPerfCmd **Launch** 選項搭配使用。  如果應用程式不是命令列應用程式，則 **Console** 沒有作用。  
  
## 語法  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### 參數  
 None  
  
## 必要選項  
 **Console** 只能在也包含 **Launch** 選項的命令列上指定。  
  
 **Launch:** `AppName`  
 啟動程式碼剖析工具以及 `AppName` 所指定的應用程式。  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)