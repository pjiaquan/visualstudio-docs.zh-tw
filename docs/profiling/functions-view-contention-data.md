---
title: "函式檢視 - 程式碼剖析工具：爭用資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "函式檢視"
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 函式檢視 - 程式碼剖析工具：爭用資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

爭用資料的 \[函式\] 報表檢視會列出執行程式碼剖析期間，遭到封鎖而無法在執行程式碼剖析期間執行的函式。  
  
 下表說明使用並行方法收集之程式碼剖析資料檔案的 \[函式\] 檢視中顯示的值。  
  
|資料行|描述|  
|---------|--------|  
|**專有封鎖時間**|此函式遭封鎖，無法在函式主體中執行程式碼的時間長度。  並不包含函式中由函式所呼叫的封鎖時間。|  
|**專有封鎖時間 %**|此函式的專有封鎖時間佔程式碼剖析執行期間所有封鎖時間的百分比。|  
|**專有爭用**|此函式遭封鎖，無法在函式主體中執行程式碼的次數。  函式所呼叫函式中的爭用不包括在內。|  
|**專有爭用 %**|在程式碼剖析執行期間，此函式的專有爭用佔所有爭用的百分比。|  
|**函式位址**|函式的位址。|  
|**函式名稱**|函式的完整名稱。|  
|**內含封鎖時間**|此函式或此函式呼叫的函式遭到封鎖而無法執行的時間。|  
|**內含封鎖時間 %**|此函式或模組的內含封鎖時間佔程式碼剖析執行期間所有封鎖時間的百分比。|  
|**內含爭用**|此函式或此函式呼叫的函式遭到封鎖而無法執行的次數。|  
|**內含爭用 %**|在程式碼剖析執行期間，此函式或模組的內含爭用佔所有爭用的百分比。|  
|**函式行號**|在原始程式檔中這個函式的開頭行號。|  
|**模組名稱**|包含該函式的模組名稱。|  
|**模組路徑**|包含該函式的模組路徑。|  
|**處理序 ID**|函式執行所在之處理序的處理序 ID \(PID\)。|  
|**處理序名稱**|處理序的名稱。|  
|**原始程式檔**|包含這個函式定義的原始程式檔。|  
  
## 請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [函式檢視](../profiling/functions-view.md)   
 [函式檢視 \- 檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [函式檢視 \- 取樣](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [函式檢視](../profiling/functions-view-instrumentation-data.md)   
 [函式檢視](../profiling/functions-view-sampling-data.md)