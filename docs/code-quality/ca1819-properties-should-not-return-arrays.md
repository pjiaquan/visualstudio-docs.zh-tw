---
title: "CA1819：屬性不應傳回陣列 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1819：屬性不應傳回陣列
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 公用型別中之公用或保護的屬性會傳回陣列。  
  
## 規則描述  
 即使屬性是唯讀，所傳回的陣列不會是寫入保護。  若要保持陣列為防止遭他人修改，屬性必須傳回陣列複本。  一般而言，使用者不了解呼叫這類屬性所造成的不良效能影響。  使用者更有可能使用屬性做為索引屬性。  
  
## 如何修正違規  
 若要修正這個規則的違規情形，請讓屬性成為方法，或是變更屬性以傳回集合。  
  
## 隱藏警告的時機  
 屬性 \(Attribute\) 可以包含傳回陣列的屬性 \(Property\)，但不能包含傳回集合的屬性 \(Property\)。  您可以隱藏針對衍生自 [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True) 類別之屬性 \(Attribute\) 的屬性 \(Property\) 所引發的警告。  否則，不要隱藏此規則的警告。  
  
## 範例違規  
  
### 描述  
 下列範例顯示違反此規則的屬性。  
  
### 程式碼  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### 註解  
 若要修正這個規則的違規情形，請讓屬性成為方法，或是變更屬性以傳回集合而非陣列。  
  
## 變更屬性為方法的範例  
  
### 描述  
 下列範例會藉由變更屬性為方法來修正違規。  
  
### 程式碼  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## 傳回集合的範例  
  
### 描述  
 下列範例會藉由變更屬性以傳回集合來修正違規。  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### 程式碼  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## 允許使用者修改屬性  
  
### 描述  
 您可能會想要允許類別消費者修改屬性。  下列範例顯示違反這個規則的讀取\/寫入屬性。  
  
### 程式碼  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### 註解  
 下列範例會藉由變更屬性以傳回 <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName> 來修正違規。  
  
### 程式碼  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## 相關規則  
 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)