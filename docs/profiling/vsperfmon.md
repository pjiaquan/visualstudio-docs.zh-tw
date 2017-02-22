---
title: "VSPerfMon | Microsoft Docs"
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
  - "VSPerfMon 工具"
  - "命令列，工具"
  - "命令列工具，VSPerfMon 工具"
  - "資料 [Visual Studio ALM]，VSPerfMon 工具"
  - "效能資料，VSPerfMon 工具"
  - "效能工具，VSPerfMon 工具"
  - "程式碼剖析工具，VSPerfCmd"
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfMon
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 VSPerfMon 工具收集應用程式的效能資料，通常這個工具是由 VSPerfCmd.exe 啟動。  VSPerfMon 會顯示關於附加處理序或卸離處理序的額外資訊，而這項資訊是使用 VSPerfCmd 工具時所無法取得的。  若要檢視這項資訊，請在另一個視窗中啟動 VSPerfMon。  若要叫用 VSPerfMon，請使用下列語法：  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 下表說明 VSPerfMon 工具的選項：  
  
|選項|說明|  
|--------|--------|  
|**U**|以 Unicode 格式撰寫已重新導向的主控台輸出。這必須是第一個指定的選項。|  
|**OUTPUT:** `<` *file name* `>`|將輸出重新導向至指定的檔案名稱。|  
|**TRACE**|啟動效能監視器進行檢測程式碼剖析。|  
|**SAMPLE**|啟動效能監視器進行取樣程式碼剖析。|  
|**COVERAGE**|啟動效能監視器進行程式碼涵蓋範圍收集。|  
|**CONCURRENCY**|啟動資源爭用程式碼剖析的效能監視器。|  
|**USER:** `[` *domain* `\]` *username*|讓用戶端從指定的帳號存取效能監視器。|  
|**CROSSSESSION**|啟用跨工作階段程式碼剖析。|  
|**COUNTER** `:cfg`|使用檢測 \(TRACE\) 程式碼剖析方法時，指定要在每個檢測點收集的 CPU 計數器。  您可以指定多個計數器選項，收集多個計數器的資料。<br /><br /> 請使用下列語法指定計數器 \(*cfg*\) 資料：<br /><br /> CounterName\[**,**Reload\[,FriendlyName\]\]<br /><br /> -   CounterName 是 VSPerfCmd \/QueryCounters 命令傳回的計數器名稱。<br />-   Reload 是計數器事件取樣間隔。  請勿搭配檢測方法使用 *Reload*。<br />-   當指定時，FriendlyName 會取代程式碼剖析工具報告欄位名稱中的CounterName。|  
|**WINCOUNTER** `:path`|指定要加入標記資料的 Windows 效能計數器。  `path` 是 PDH 計數器路徑格式的 Windows 效能計數器字串。  例如：<br /><br /> \\Processor\(0\)\\% Processor Time<br /><br /> \\System\\Context Switches\/sec|  
|**AUTOMARK** `:n`|指定使用 \/WINCOUNTER 時自動標記的間隔時間 \(以毫秒為單位\)。  四捨五入到最接近的 500 毫秒數。<br /><br /> 請使用 0 來停用自動標記 \(如果未指定，預設值 \= 500 毫秒\)|  
  
## 請參閱  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [程式碼剖析工具報表檢視](../profiling/performance-report-views.md)