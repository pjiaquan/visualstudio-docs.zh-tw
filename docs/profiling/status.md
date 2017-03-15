---
title: "Status | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Status
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Status** 選項會程式碼剖析工具的狀態，以及目前正在進行程式碼剖析之處理序的相關資訊。  
  
 **Status** 選項必須是命令列上指定的唯一選項。  程式碼剖析工具必須以 VSPerfCmd.exe **Start** 選項來初始化，才能顯示任何狀態。  
  
## 語法  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### 參數  
 None  
  
## 備註  
 **Status** 選項會顯示下列程式碼剖析工具的狀態資訊。  
  
 **Output File Name**  
 目前程式碼分析工具資料檔的檔案名稱和路徑。  
  
 **Collection Mode**  
 SAMPLE 或 TRACE。  
  
 **Maximum Processes**  
 取得或設定可同時處於作用中之更新執行緒數目的最大值。可同時進行分析的處理序數目上限，以及目前作用中的處理序數目。  
  
 **Maximum Threads**  
 可同時分析的執行緒之數目上限。  
  
 **Number of Buffers**  
 專用於撰寫程式碼剖析資料的記憶體緩衝區數目。  
  
 **Size of Buffers**  
 記憶體緩衝區的位元組大小。  
  
 **Status** 選項會顯示下列狀態資訊，是目前正在進行分析的每一個處理序的資訊。  
  
 **Process**  
 受到剖析的處理序名稱。  
  
 **Process ID**  
 處理序的系統識別項。  
  
 **Num Threads**  
 目前執行中的執行緒數目。  
  
 **Start\/Stop Count**  
 主要內部程式碼剖析工具計數，以控制此處理序的資料收集。  計數必須等於一，才能收集資料。  Start\/Stop 計數可以透過程式碼分析工具 API 及 VSPerfCmd 選項 **GlobalOn**、**GlobalOff**、**ProcessOn**、**ProcessOff**、**ThreadOn** 和 **ThreadOff** 來控制。  
  
 **Suspend\/Resume Count**  
 次要內部程式碼剖析工具計數，以控制此處理序的資料收集。  此計數必須小於或等於零，才能收集資料。  **Suspend\/Resume** 計數只能透過程式碼分析工具 API 來控制。  
  
 **Users with access rights to monitor**  
 列出擁有程式碼剖析工具的存取權之使用者名稱。  使用 VSPerfCmd.exe **Admin** 選項，可以授權其他使用者存取權。  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)