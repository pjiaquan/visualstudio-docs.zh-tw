---
title: "CA1043：必須針對索引子使用整數類或字串引數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1043：必須針對索引子使用整數類或字串引數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別所包含之公用或保護的索引子，使用了 <xref:System.Int32?displayProperty=fullName>、<xref:System.Int64?displayProperty=fullName>、<xref:System.Object?displayProperty=fullName> 或 <xref:System.String?displayProperty=fullName> 以外的索引型別。  
  
## 規則描述  
 索引子 \(也就是索引的屬性\) 應該使用整數型別 \(Integer Type\) 或字串型別的索引。  這些型別通常會用於資料結構的索引，並且可以提升程式庫的可用性。  <xref:System.Object> 型別的使用應限制於無法在設計階段指定特定整數型別或字串型別的情況。  如果設計需要使用其他型別的索引，請考慮該型別是否表示邏輯資料存放區。  如果不表示邏輯資料存放區的話，請使用方法。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將索引變更為整數型別或字串型別，或使用方法來替代索引子。  
  
## 隱藏警告的時機  
 只有在仔細考慮確實需要非標準索引子之後，才能隱藏此規則的警告。  
  
## 範例  
 在下列範例中，程式碼會顯示使用 <xref:System.Int32> 索引的索引子。  
  
 [!CODE [FxCop.Design.IntegralOrStringIndexers#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers#1)]  
  
## 相關規則  
 [CA1023：不應該使用多維索引子](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)