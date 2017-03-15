---
title: "CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **CrossSession** 選項可讓程式碼剖析工具收集任何主控台工作階段中的資料。  **CrossSession** 選項必須與 **Start** 選項一起使用。  
  
 您可以使用縮寫 **CS** 來取代 **CrossSession**。  
  
## 語法  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### 參數  
 None  
  
## 有效的選項  
 若要在另一個工作階段中啟用程式碼剖析，就必須以 **Start** 選項來指定 **CrossSession** 選項。  **CrossSession** 也必須在任何後續 **VSPerfCmd Attach** 和 **Detach** 命令中指定。  
  
 **Start:** `Method`  
 **Start** 選項會將程式碼剖析工具初始化成指定的程式碼剖析方法。  
  
 **Attach:** *PID*\[**,***PID*\]  
 開始對指定的處理序執行程式碼剖析。  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 停止對指定的處理序進行程式碼剖析。  
  
## 範例  
 這個範例中，**CrossSession** 選項是用來附加至在另一個主控台工作階段中啟動的應用程式。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)