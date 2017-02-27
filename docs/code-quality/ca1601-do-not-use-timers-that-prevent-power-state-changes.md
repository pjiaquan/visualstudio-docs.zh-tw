---
title: "CA1601：不要使用會妨礙電源狀態變更的計時器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1601：不要使用會妨礙電源狀態變更的計時器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|分類|Microsoft.Mobility|  
|中斷變更|中斷|  
  
## 原因  
 計時器的間隔是設定成每秒引發數次。  
  
## 規則描述  
 輪詢頻率不要超過每秒一次，也不要使用每秒引發一次以上的計時器。  更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。  
  
## 如何修正違規  
 將計時器間隔設定成每秒引發一次以下。  
  
## 隱藏警告的時機  
 只有在每秒必須多次引發計數器，且可以放心地忽略行動力的考量時，才能隱藏這項規則。