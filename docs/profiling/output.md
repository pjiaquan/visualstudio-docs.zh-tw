---
title: "輸出 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 輸出
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Output** 選項會指定效能工作階段之分析資料檔案的名稱。  **Output** 必須與 **Start** 選項搭配使用。  
  
## 語法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### 參數  
 `FileName`  
 資料檔案的名稱。  接受完整與部分路徑。  如果未指定路徑，則會在目前目錄中建立檔案。  
  
## 必要選項  
 **Output** 選項必須與 **Start** 選項一起使用。  
  
 **Start:** `Method`  
 指定輸出檔名稱。  
  
## 範例  
 下列範例會在目前目錄中建立程式碼剖析資料檔案。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)