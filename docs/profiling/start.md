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
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 啟動
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Start** 選項是 VSPerfCmd.exe 選項，會將程式碼剖析工具初始化成指定的程式碼剖析方法。  
  
## 語法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### 參數  
 `Method`  
 必須是下列其中一個關鍵字：  
  
-   **TRACE** \- 指定檢測方法。  
  
-   **SAMPLE** \- 指定取樣方法。  
  
-   **COVERAGE** \- 指定程式碼涵蓋範圍。  
  
-   **CONCURRENCY** \-指定資源爭用方法。  
  
## 必要選項  
 當命令列上指定了 **Start** 時，必須指定 **Output** 選項。  
  
 **Output:** `filename`  
 指定輸出檔名稱。  
  
## 專有選項  
 下列選項只能在命令列中搭配 **Start** 選項使用。  
  
 **CrossSession**&#124;**CS**  
 啟用跨處理序 \(Cross\-Process\) 程式碼剖析。  支援選項名稱 **CrossSession** 和 **CS**。  
  
 **User:**\[`domain\`\]`username`  
 讓用戶端從指定的帳號存取監視器。  
  
 **WinCounter:** `Path` \[**Automark**:`n`\]  
 **WinCounter** 會指定將 Windows 效能計數器包括為程式碼剖析資料檔中的標記。  **AutoMark** 會以毫秒為單位，指定資料檔之集合之間的間隔。  
  
## 無效的選項  
 下列選項不能在命令列中搭配 **Start** 選項使用。  
  
 **Status**  
 **Status** 套用至這些已經過程式碼剖析的處理序。  它會列出處理序和執行緒，以及這些處理序和執行緒目前的程式碼剖析狀態 \(開啟\/關閉\)。  例如，如果處理序已停止，**Status** 將不會在報表中指出這點。  **Status** 會顯示這個處理序為已經過程式碼剖析或尚未經過程式碼剖析。  
  
 **Shutdown**\[**:**`Timeout`\]  
 關閉程式碼剖析工具。  
  
## 範例  
 下列範例示範如何使用 VSPerfCmd.exe **Start** 選項來初始化程式碼剖析工具。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)