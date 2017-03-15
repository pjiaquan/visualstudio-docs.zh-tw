---
title: "CA1035：ICollection 實作包含強類型成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1035：ICollection 實作包含強類型成員
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別會實作 <xref:System.Collections.ICollection?displayProperty=fullName>，但不會提供 <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> 的強型別 \(Strongly Typed\) 方法。  <xref:System.Collections.ICollection.CopyTo%2A> 的強型別版本必須接受兩個參數，而且不能以 <xref:System.Array?displayProperty=fullName> 或 <xref:System.Object?displayProperty=fullName> 的陣列做為它的第一個參數。  
  
## 規則描述  
 這項規則要求 <xref:System.Collections.ICollection> 實作提供強型別成員，讓使用者在使用介面所提供的功能時，不需將引數轉換為 <xref:System.Object> 型別。  此規則假設實作 <xref:System.Collections.ICollection> 的型別會以這種方式，管理強於 <xref:System.Object> 之型別的執行個體 \(Instance\) 集合。  
  
 <xref:System.Collections.ICollection> 會實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 介面。  如果集合中的物件會擴充 <xref:System.ValueType?displayProperty=fullName>，您就必須提供 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 的強型別成員，才能避免因 Boxing 而導致的效能降低。  當集合的物件是參考型別時，這是不必要。  
  
 若要實作介面成員的強型別版本，請使用 `InterfaceName.InterfaceMemberName` 表單中的名稱 \(如 <xref:System.Collections.ICollection.CopyTo%2A>\) 明確實作介面成員。  明確介面成員會使用介面所宣告的資料型別。  使用介面成員名稱實作強型別成員，如 <xref:System.Collections.ICollection.CopyTo%2A>。  將強型別成員宣告為公用，並將參數和傳回值宣告為集合所管理的強型別。  強型別會取代較弱式型別，例如介面所宣告的 <xref:System.Object> 和 <xref:System.Array>。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請明確實作介面成員 \(將介面成員宣告為 <xref:System.Collections.ICollection.CopyTo%2A>\)。  加入公用的強型別成員、宣告為 `CopyTo`，並且以強型別陣列做為它的第一個參數。  
  
## 隱藏警告的時機  
 如果您實作新的物件架構集合 \(例如二進位樹狀目錄\)，且其中擴充新集合的型別會判斷強型別時，請隱藏這項規則的警告。  這些型別應該遵守這項規則並公開 \(Expose\) 強型別成員。  
  
## 範例  
 下列範例會實作 <xref:System.Collections.ICollection> 的正確方式。  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## 相關規則  
 [CA1038：列舉程式應該是強類型](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039：清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## 請參閱  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>