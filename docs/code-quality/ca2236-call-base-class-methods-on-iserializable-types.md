---
title: "CA2236：必須呼叫 ISerializable 類型上的基底類別方法 | Microsoft Docs"
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
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2236：必須呼叫 ISerializable 類型上的基底類別方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 型別衍生自實作 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面的型別，而且符合下列其中一個條件：  
  
-   此型別會實作序列化 \(Serialization\) 建構函式 \(Constructor\)，亦即，具有 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>、<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 參數簽章的建構函式，但是不會呼叫基底型別 \(Base Type\) 的序列化建構函式。  
  
-   此型別會實作 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 方法，但不會呼叫基底型別的 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法。  
  
## 規則描述  
 在自訂序列化處理序 \(Process\) 中，型別會實作 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法，序列化它的欄位及序列化建構函式，以便將欄位還原序列化。  如果型別是衍生自實作 <xref:System.Runtime.Serialization.ISerializable> 介面的型別，則應會呼叫基底型別 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法和序列化建構函式，以便將基底型別的欄位序列化\/還原序列化。  否則，無法將該型別正確地序列化和還原序列化。  請注意，如果衍生型別 \(Derived Type\) 沒有加入任何新的欄位，則型別不需實作 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法，也不需實作序列化建構函式，或呼叫基底型別對等用法。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請從對應的衍生型別方法或建構函式，呼叫基底型別 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法或序列化建構函式。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會呼叫基底類別的序列化建構函式和 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法，以顯示滿足規則的衍生型別。  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## 相關規則  
 [CA2240：必須正確實作 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：請實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：請正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237：必須以 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120：必須保護序列化建構函式](../Topic/CA2120:%20Secure%20serialization%20constructors.md)