---
title: "CA1600：不要使用 Idle 處理序優先權 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1600：不要使用 Idle 處理序優先權
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|分類|Microsoft.Mobility|  
|中斷變更|中斷|  
  
## 原因  
 當處理序設定為 `ProcessPriorityClass.Idle` 時，會引發這項規則。  
  
## 規則描述  
 請勿將處理序優先權設定為 Idle。  具有 `System.Diagnostics.ProcessPriorityClass.Idle` 的處理序會在應該閒置的時候佔用 CPU，因而阻礙 CPU 待命。  
  
## 如何修正違規  
 將處理序設定為 `ProcessPriorityClass.BelowNormal`。  
  
## 隱藏警告的時機  
 在必須有 Idle 處理序優先權，而且可以放心地忽略行動力考量時，才能隱藏這項規則。