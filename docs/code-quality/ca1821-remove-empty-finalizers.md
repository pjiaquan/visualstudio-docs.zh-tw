---
title: "CA1821：必須移除空的完成項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RemoveEmptyFinalizers"
  - "CA1821"
helpviewer_keywords: 
  - "CA1821"
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1821：必須移除空的完成項
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 型別實作空白的完成項，只呼叫基底型別完成項，或是只呼叫依條件發出的方法。  
  
## 規則描述  
 請盡可能避免使用完成項，因為追蹤物件存留期 \(Lifetime\) 時將會產生額外的效能負荷。  記憶體回收行程會在回收物件之前執行完成項。  這表示它必須執行兩次回收作業才能回收物件。  空白完成項只會增加這種額外負荷，而沒有任何好處。  
  
## 如何修正違規  
 移除空白完成項。  如果需要有完成項才能進行偵錯，請將整個完成項包含在 `#if DEBUG / #endif` 指示詞中。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的訊息。  無法抑制最終化將會降低效能且不提供任何好處。  
  
## 範例  
 下列範例顯示應該移除的空白完成項、應該包含在 `#if DEBUG / #endif` 指示詞中的完成項，以及正確使用 `#if DEBUG / #endif` 指示詞的完成項。  
  
 [!code-cs[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]