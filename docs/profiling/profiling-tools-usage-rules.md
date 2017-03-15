---
title: "程式碼剖析工具使用規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 程式碼剖析工具使用規則
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

程式碼剖析工具使用分類中的效能規則會提供以最有效方式使用分析工具來收集資料的指引。  
  
|||  
|-|-|  
|[DA0002：遺漏 VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|命令列程式碼剖析可能包含不完整的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 二進位檔資料。  這可能是因為沒有設定正確的環境變數所造成。|  
|[DA0003：許多核心樣本](../profiling/da0003-many-kernel-samples.md)|已記錄許多在目標二進位檔執行範圍以外出現的程式碼剖析樣本。  若要收集更精確的資料，請考慮使用檢測方法。|  
|[DA0004：處理器使用率高](../profiling/da0004-high-processor-usage.md)|程式碼剖析資料建議指出，在程式碼剖析回合期間，處理器一直處於忙碌狀態。  若要收集更精確的資料，請考慮使用取樣方法。|  
|[DA0008：收集的樣本少](../profiling/da0008-few-samples-collected.md)|在程式碼剖析回合中所收集的樣本數目不夠高，無法產生統計上的意義。  請考慮再次進行程式碼剖析，並讓應用程式執行較長的時間。  您也可以考慮使用檢測方法來收集資料。|  
|[DA0026：過多核心 CPU 時間處理](../Topic/DA0026:%20Excessive%20kernel%20CPU%20time%20processing.md)|在程式碼剖析回合中，相當長的時間是以處理器核心模式進行。  請考慮使用系統呼叫做為度量而非使用時間做為度量，進行取樣。|  
|[DA0029：不支援的 CLR 版本](../profiling/da0029-unsupported-clr-version.md)|進行程式碼剖析的二進位檔正在使用分析工具不支援的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。  分析工具報告無法解析符號名稱。|  
|[DA0030：蒐集資料庫專案的階層互動度量](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|已收集 <xref:System.Data?displayProperty=fullName> 命名空間中的大量方法呼叫。  若要加入有關資料庫呼叫的資料，請考慮在程式碼剖析回合中收集階層互動資料。|