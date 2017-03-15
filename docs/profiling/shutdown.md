---
title: "關機 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 關機
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Shutdown** 選項會等候所有目前正在進行程式碼剖析的處理序結束或中斷連結，然後才關閉程式碼剖析工具並關閉程式碼剖析資料檔案。  **Shutdown** 選項必須是執行程式碼剖析的最後一個命令。  
  
 如果未指定逾時參數，則 **Shutdown** 選項會無限期等候。  如果已指定逾時參數，則此選項會在指定的秒數之後傳回，而不會關閉程式碼剖析工具或關閉資料檔案。  
  
 **Shutdown** 選項必須是命令列上指定的唯一選項。  
  
## 語法  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### 參數  
 `Timeout`  
 -   \(選擇性\) 如果已指定，則此選項會在指定的秒數之後傳回，而不會關閉程式碼剖析工具或關閉程式碼剖析資料檔案。  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)