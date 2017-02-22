---
title: "函式檢視 - 程式碼剖析工具：.NET 記憶體取樣資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "函式檢視"
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 函式檢視 - 程式碼剖析工具：.NET 記憶體取樣資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用取樣方法收集之 .NET 記憶體配置程式碼剖析資料的 \[函式\] 檢視，會列出在執行程式碼剖析期間配置記憶體的函式，並且回報配置的大小和數量。  
  
|資料行|描述|  
|---------|--------|  
|**處理序 ID**|執行程式碼剖析期間的處理序 ID \(PID\)。|  
|**處理序名稱**|處理序的名稱。|  
|**模組名稱**|包含該函式的模組名稱。|  
|**模組路徑**|包含該函式的模組路徑。|  
|**原始程式檔**|包含這個函式定義的原始程式檔。|  
|**函式名稱**|函式的完整名稱。|  
|**函式行號**|在原始程式檔中這個函式的開頭行號。|  
|**函式位址**|函式的位址。|  
|**內含配置**|這個函式及其子函式中已配置的物件總數。|  
|**內含配置 %**|執行程式碼剖析期間內，此函式的內含配置佔所有已配置物件的百分比。|  
|**專有配置**|在呼叫堆疊頂端直接執行函式時所建立的物件數目。  此數目不包含子函式中已建立的物件。|  
|**專有配置 %**|在執行程式碼剖析期間內，此函式的專有配置佔所有已配置物件的百分比。|  
|**內含位元組**|這個函式及其子函式所配置的記憶體位元組數。|  
|**內含位元組 %**|執行程式碼剖析期間內，此函式的內含配置佔所有已配置記憶體位元組的百分比。|  
|**專有位元組**|這個函式所配置的記憶體位元組數，但不包含其子函式配置的記憶體位元組數。|  
|**專有位元組 %**|執行程式碼剖析期間內，此函式的專有位元組佔所有已配置記憶體位元組的百分比。|  
  
## 請參閱  
 [函式檢視 \- 檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [函式檢視](../profiling/functions-view-sampling-data.md)   
 [函式檢視](../profiling/functions-view-instrumentation-data.md)