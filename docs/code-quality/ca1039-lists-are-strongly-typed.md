---
title: "CA1039：清單為強類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1039：清單為強類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別會實作 <xref:System.Collections.IList?displayProperty=fullName>，但不會針對下列的一或多個項目提供強型別方法：  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## 規則描述  
 這項規則要求 <xref:System.Collections.IList> 實作提供強型別成員，讓使用者在使用介面所提供的功能時，不需將引數轉換為 <xref:System.Object?displayProperty=fullName> 型別。  <xref:System.Collections.IList> 介面是由可透過索引存取的物件集合所實作。  這項規則假設實作 <xref:System.Collections.IList> 的型別的確會這樣做，以管理比 <xref:System.Object> 還強之型別的執行個體 \(Instance\) 集合。  
  
 <xref:System.Collections.IList> 會實作 <xref:System.Collections.ICollection?displayProperty=fullName> 和 <xref:System.Collections.IEnumerable?displayProperty=fullName> 介面。  若要實作 <xref:System.Collections.IList>，您必須針對 <xref:System.Collections.ICollection> 提供必要的強型別成員。  如果集合中的物件會擴充 <xref:System.ValueType?displayProperty=fullName>，則您必須針對 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 提供強型別成員，以避免因 Boxing 而導致效能降低，但當集合的物件是參考型別 \(Reference Type\) 時，則不需如此。  
  
 若要遵守這項規則，請使用 InterfaceName.InterfaceMemberName 格式的名稱，明確地實作介面成員，如 <xref:System.Collections.IList.Add%2A>。  明確介面成員會使用介面所宣告的資料型別。  使用介面成員名稱實作強型別成員，如 `Add`。  將強型別成員宣告為公用，並將參數和傳回值宣告為集合所管理的強型別。  強型別會取代較弱式型別，例如介面所宣告的 <xref:System.Object> 和 <xref:System.Array>。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請明確地實作 <xref:System.Collections.IList> 成員，並提供強型別成員取代先前所提到的成員。  如需正確實作 <xref:System.Collections.IList> 介面並提供必要強型別成員的程式碼，請參閱下列範例。  
  
## 隱藏警告的時機  
 在實作新的物件架構集合 \(如連結串列 \(Linked List\)\)，且其中擴充新集合的型別會判斷強型別時，請隱藏這項規則的警告。  這些型別應該遵守這項規則並公開 \(Expose\) 強型別成員。  
  
## 範例  
 在下列範例中，型別 `YourType` 會擴充 <xref:System.Collections.CollectionBase?displayProperty=fullName>，如同所有強型別集合所應該做的一般。  請注意，<xref:System.Collections.CollectionBase> 會為您提供 <xref:System.Collections.IList> 介面的明確實作。  因此，您只能 <xref:System.Collections.IList> 及 <xref:System.Collections.ICollection> 的強型別成員。  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## 相關規則  
 [CA1035：ICollection 實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038：列舉程式應該是強類型](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## 請參閱  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>