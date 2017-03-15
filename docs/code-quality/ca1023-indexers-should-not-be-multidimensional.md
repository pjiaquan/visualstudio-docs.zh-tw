---
title: "CA1023：不應該使用多維索引子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1023：不應該使用多維索引子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 public 或 protected 型別包含使用一個以上之索引的公用或保護之索引子 \(Indexer\)。  
  
## 規則描述  
 索引子 \(也就是索引屬性\) 應使用單一索引。  多維式索引子會大幅降低程式庫的可用性。  如果設計需要多個索引，請考慮該型別是否代表邏輯資料存放區。  如果不是，請使用方法。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將設計變更為使用長整數 \(Long Integer\) 或字串索引，或是改用方法而非索引子。  
  
## 隱藏警告的時機  
 只有在仔細考慮確實需要非標準索引子之後，才能隱藏此規則的警告。  
  
## 範例  
 下列範例所顯示的型別 `DayOfWeek03`，它的多維式索引子會違反規則。  該索引子可視為轉換型別，因此公開為方法較為適當。  該型別會在 `RedesignedDayOfWeek03` 中重新設計以滿足規則。  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## 相關規則  
 [CA1043：必須針對索引子使用整數類或字串引數](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)