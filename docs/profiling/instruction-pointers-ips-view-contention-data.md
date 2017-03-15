---
title: "指令指標 (IP) 檢視 - 程式碼剖析工具：爭用資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "指令指標檢視"
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 指令指標 (IP) 檢視 - 程式碼剖析工具：爭用資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

爭用資料的 IP 檢視會列出在執行程式碼剖析期間遭到封鎖而無法執行之組件指令的資料。  
  
 下表說明 \[指令指標\] 檢視中資料行的值。  
  
|資料行|描述|  
|---------|--------|  
|**專有封鎖時間**|此函式中的封鎖時間。|  
|**專有封鎖時間 %**|執行指令時，封鎖時間的百分比。|  
|**專有爭用**|執行指令時，發生爭用的次數。|  
|**專有爭用 %**|執行指令時，在執行程式碼剖析期間發生之所有爭用的百分比。|  
|**函式位址**|載入的二進位檔案中，函式的起始記憶體位址。|  
|**函式名稱**|包含指令之函式的名稱。|  
|**指令位址**|載入的二進位檔案中指令的記憶體位址。|  
|**函式行號**|在原始程式檔中這個函式的開頭行號。|  
|**模組名稱**|包含指令的模組名稱。|  
|**模組路徑**|包含指令的模組路徑。|  
|**處理序 ID**|已進行程式碼剖析之處理序的處理序 ID \(PID\)。|  
|**處理序名稱**|處理序的名稱。|  
|**原始程式碼開頭字元**|此指令起始之原始程式檔程式行中字元的位移。|  
|**原始程式碼結尾字元**|此指令結束之原始程式檔程式行中字元的位移。|  
|**原始程式檔**|包含指令的原始程式檔。|  
|**原始程式碼開頭行**|在原始程式檔中，此指令起始的行號。|  
|**原始程式碼結尾行**|在原始程式檔中，此指令結束的行號。|  
  
## 請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [指令指標 \(IP\) 檢視](../profiling/instruction-pointers-ips-view.md)   
 [指令指標 \(IP\) 檢視 \- 取樣](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [指令指標 \(IP\) 檢視](../profiling/instruction-pointers-ips-view-sampling-data.md)