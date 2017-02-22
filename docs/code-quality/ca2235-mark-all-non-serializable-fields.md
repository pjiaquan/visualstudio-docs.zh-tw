---
title: "CA2235：必須標記所有不可序列化的欄位 | Microsoft Docs"
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
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2235：必須標記所有不可序列化的欄位
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 可序列化之型別中所宣告之型別的執行個體 \(Instance\) 欄位是不可序列化的。  
  
## 規則描述  
 可序列化型別是以 <xref:System.SerializableAttribute?displayProperty=fullName> 屬性 \(Attribute\) 標示的型別。  當型別序列化時，如果型別所包含的不是可序列化之型別的執行個體欄位，將會發生 <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> 例外狀況。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將 <xref:System.NonSerializedAttribute?displayProperty=fullName> 屬性套用到不可序列化的欄位。  
  
## 隱藏警告的時機  
 只有在宣告的 <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> 型別允許欄位的執行個體成為序列化或還原序列化時，才能隱藏這項規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的型別和滿足規則的型別。  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## 相關規則  
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240：必須正確實作 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：請實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：請正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237：必須以 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120：必須保護序列化建構函式](../Topic/CA2120:%20Secure%20serialization%20constructors.md)