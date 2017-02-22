---
title: "處理序檢視 - 程式碼剖析工具：爭用資料 | Microsoft Docs"
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
  - "處理序檢視"
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 處理序檢視 - 程式碼剖析工具：爭用資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[處理序\] 檢視會顯示程式碼剖析執行期間所執行之處理序和執行緒的爭用資料。  
  
 當有符號可用時，處理序會依名稱列出。  若沒有符號可以使用，處理序會依它們的記憶體位址，以十六進位格式列出。  執行緒會列為建立它們之處理序的子項目。  
  
 下表說明 \[處理序\] 檢視資料表中資料行的值。  
  
|資料行|描述|  
|---------|--------|  
|**開始時間**|毫秒數，或者從程式碼剖析開始到處理序或執行緒的處理器循環。|  
|**封鎖時間**|處理序或執行緒的函式遭封鎖而無法執行的時間總計。|  
|**封鎖時間 %**|處理序或執行緒的函式遭封鎖而無法執行的處理序或執行緒存留期百分比。|  
|**爭用**|處理序或執行緒的函式遭封鎖而無法執行的次數。|  
|**爭用 %**|在執行程式碼剖析期間，處理序或執行緒的爭用佔所有爭用的百分比。|  
|**結束時間**|毫秒數，或者從程式碼剖析結束到處理序或執行緒的處理器循環。|  
|**ID**|由系統產生的處理序或執行緒識別項。|  
|**存留時間**|從處理序或執行緒開始到結束，或是到程式碼剖析結束的毫秒數或處理器循環。|  
|**型別**|資料列的類型，為處理序或執行緒。<br /><br /> 只存在於 **VSReport** 命令列報告中。  如需詳細資訊，請參閱[VSPerfReport](../profiling/vsperfreport.md)。|  
|**名稱**|處理序或執行緒的名稱。|  
|**唯一的 ID**|程式碼分析工具產生的識別項，對於處理序或執行緒而言具有唯一性。|  
  
## 請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [處理序檢視](../profiling/process-view.md)