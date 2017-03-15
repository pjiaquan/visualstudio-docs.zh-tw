---
title: "記憶體和分頁效能規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 記憶體和分頁效能規則
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

記憶體和分頁分類中的效能規則會識別程式碼剖析回合中可能影響應用程式效能和回應速度的分頁活動。  
  
|||  
|-|-|  
|[DA0014：極高比率的使用中記憶體分頁到磁碟](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)|在整個程式碼剖析回合期間發生非常高比率的作用中記憶體對磁碟的來回分頁。  這個層級的分頁比率通常會影響應用程式效能和回應速度。  請考慮修訂演算法來降低記憶體配置。  您可能也必須考慮應用程式的記憶體需求。  請嘗試在具有更多記憶體的電腦上，再次執行程式碼剖析。  當分頁活動的數量超過規則 D0017 的臨界值上限時，就會引發此規則。|  
|[DA0017：作用中的記憶體分頁至磁碟的比率很高](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|在整個程式碼剖析回合期間發生相當高比率的作用中記憶體對磁碟的來回分頁。  這個層級的分頁比率通常會影響應用程式效能和回應速度。  請考慮修訂演算法來降低記憶體配置。  您可能也必須考慮應用程式的記憶體需求。  請嘗試在具有更多記憶體的電腦上，再次執行程式碼剖析。|