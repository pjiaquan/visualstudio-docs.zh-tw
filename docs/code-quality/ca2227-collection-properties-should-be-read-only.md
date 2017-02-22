---
title: "CA2227：集合屬性應該為唯讀 | Microsoft Docs"
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
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2227：集合屬性應該為唯讀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|分類|Microsoft.Usage|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的可寫入屬性 \(Property\) 是實作 <xref:System.Collections.ICollection?displayProperty=fullName> 的型別。  此規則會忽略陣列、包含名為 'Item' 屬性的索引子 \(Indexer\)，以及使用權限集合。  
  
## 規則描述  
 可寫入的集合屬性允許使用者以完全不同的集合來取代該集合。  唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。  如果目標是取代集合，則慣用的設定模式會包含可從集合中移除所有項目的方法，以及重新填入集合的方法。  如需此模式的範例，請參閱 <xref:System.Collections.ArrayList?displayProperty=fullName> 類別的 <xref:System.Collections.ArrayList.Clear%2A> 和 <xref:System.Collections.ArrayList.AddRange%2A> 方法。  
  
 二進位和 XML 序列化 \(Serialization\) 都支援唯讀屬性 \(屬性為集合\)。  <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 類別具有型別的特定要求，會實作 <xref:System.Collections.ICollection> 和 <xref:System.Collections.IEnumerable?displayProperty=fullName>，以便進行序列化。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請讓屬性為唯讀的，而且如果設計需要用到它，則加入方法以便清除並重新填入集合。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示含可寫入之集合屬性的型別，以及如何直接取代集合。  此外，也會顯示使用 `Clear` 和 `AddRange` 方法取代唯讀集合屬性的慣用方式。  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## 相關規則  
 [CA1819：屬性不應傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)