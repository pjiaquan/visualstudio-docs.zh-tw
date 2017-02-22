---
title: "CA1038：列舉程式應該是強類型 | Microsoft Docs"
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
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1038：列舉程式應該是強類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別會實作 <xref:System.Collections.IEnumerator?displayProperty=fullName>，但不提供 <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> 屬性的強型別 \(Strongly Typed\) 版本。  衍生自下列型別的型別不受限於此規則：  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## 規則描述  
 此規則需要 <xref:System.Collections.IEnumerator> 實作才能同時提供 <xref:System.Collections.IEnumerator.Current%2A> 屬性的強型別版本，如此當使用者使用介面提供的功能時，就不需要將傳回值轉換為強型別。  此規則會假設實作 <xref:System.Collections.IEnumerator> 的型別包含型別的執行個體 \(Instance\) 集合，且該型別強過 <xref:System.Object>。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請明確實作介面屬性 \(將該屬性宣告為 `IEnumerator.Current`\)。  加入宣告為 `Current` 的屬性公用強型別版本，並傳回強型別物件。  
  
## 隱藏警告的時機  
 在實作物件架構列舉值以便與物件架構集合搭配使用時 \(例如二進位樹狀目錄\)，請排除此規則的警告。  擴充新集合的型別將定義強型別列舉值，並公開 \(Expose\) 強型別屬性。  
  
## 範例  
 下列範例會實作強型別 <xref:System.Collections.IEnumerator> 型別的正確方法。  
  
 [!CODE [FxCop.Design.IEnumeratorStrongTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes#1)]  
  
## 相關規則  
 [CA1035：ICollection 實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039：清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## 請參閱  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>