---
title: "CA2237：必須以 SerializableAttribute 標記 ISerializable 類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2237：必須以 SerializableAttribute 標記 ISerializable 類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 外部可見的型別會實作 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面，而且型別並未以 <xref:System.SerializableAttribute?displayProperty=fullName> 屬性 \(Attribute\) 標記。  此規則會忽略基底型別 \(Base Type\) 未序列化的衍生型別 \(Derived Type\)。  
  
## 規則描述  
 若要讓 Common Language Runtime 辨認為可序列化，即使型別透過 <xref:System.Runtime.Serialization.ISerializable> 介面的實作使用自訂序列化常式，型別仍必須以 <xref:System.SerializableAttribute> 屬性標記。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將 <xref:System.SerializableAttribute> 屬性套用到型別。  
  
## 隱藏警告的時機  
 請勿針對例外狀況 \(Exception\) 類別 \(Class\) 隱藏此規則的警告，因為這些類別必須為可序列化，才能在不同的應用程式定義域上正常運作。  
  
## 範例  
 下列範例顯示違反規則的型別。  取消註解 <xref:System.SerializableAttribute> 屬性行，以滿足此規則。  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## 相關規則  
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240：必須正確實作 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：請實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：請正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120：必須保護序列化建構函式](../Topic/CA2120:%20Secure%20serialization%20constructors.md)