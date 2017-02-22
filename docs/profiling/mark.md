---
title: "標記 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 標記
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Mark** 選項會將指定的資訊插入程式碼剖析資料檔案。  標記可在個別的 VSPerfReport 報告中列出，或是在程式碼剖析工具 UI 的 \[標記報告\] 檢視中出現。  **Mark** 可用來指定報告和檢視篩選條件中的起點和終點。  
  
 **Mark** 選項必須是命令列上指定的唯一選項。  
  
## 語法  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### 參數  
 `MarkID`  
 使用者定義的整數，列為分析工具檢視和報表中的標記 ID。  `MarkID` 不必是唯一的。  
  
 `MarkName`  
 \(選擇項\) 在程式碼剖析工具的檢視和報告中列為 \[標記名稱\] 的使用者定義字串。  如果未指定 `MarkName`，則標記清單的 \[標記名稱\] 欄位會是空的。  以引號括住包含空格或正斜線 \("\/"\) 的字串。  
  
## 範例  
 這個範例會插入 ID 為 123 且標記名稱為 "TestMark" 的標記。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)