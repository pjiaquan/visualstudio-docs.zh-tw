---
title: "CA1010：集合應該實作泛型介面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1010：集合應該實作泛型介面
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的型別會實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 介面，但不會實作 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 介面，而且包含組件 \(Assembly\) 會以 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 為目標。  這個規則會忽略實作 <xref:System.Collections.IDictionary?displayProperty=fullName> 的型別。  
  
## 規則描述  
 若要放寬集合的可用性，請實作其中一個泛型集合介面。  然後，使用該集合填入 \(Populate\) 泛型集合型別 \(例如下列項目\)：  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## 如何修正違規  
 若要修正這個規則的違規情形，請實作下列其中一個泛型集合介面：  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## 隱藏警告的時機  
 請放心地隱藏這個規則的警告，不過，該集合的使用將會更受限制。  
  
## 範例違規  
  
### 描述  
 下列範例顯示衍生自違反此規則的非泛型 `CollectionBase` 類別的類別 \(參考型別\)。  
  
### 程式碼  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### 註解  
 若要修正這個規則的違規，應該實作泛型介面或將基底類別 \(Base Class\) 變更為已經實作泛型和非泛型介面 \(例如 `Collection<T>` 類別\) 的型別。  
  
## 藉由基底類別變更進行修正  
  
### 描述  
 下列範例藉由將集合的基底類別從非泛型 `CollectionBase` 類別變更為泛型 `Collection<T>` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `Collection(Of T)`\) 類別來修正違規。  
  
### 程式碼  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### 註解  
 對現有消費者而言，變更已發行類別的基底類別可視為重大變更。  
  
## 藉由介面實作進行修正  
  
### 描述  
 下列範例會藉由實作這些泛型介面修正違規：`IEnumerable<T>`、`ICollection<T>` 和 `IList<T>` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `IEnumerable(Of T)`、`ICollection(Of T)` 和 `IList(Of T)`\)。  
  
### 程式碼  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## 相關規則  
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公開泛型清單](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)