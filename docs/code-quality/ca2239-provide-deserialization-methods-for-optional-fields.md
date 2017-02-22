---
title: "CA2239：必須為選擇性欄位提供還原序列化方法 | Microsoft Docs"
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
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2239：必須為選擇性欄位提供還原序列化方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 型別具有以 <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> 屬性 \(Attribute\) 標示的欄位，而且型別不提供還原序列化 \(Deserialization\) 事件處理方法。  
  
## 規則描述  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 屬性對於序列化 \(Serialization\) 沒有作用，而以屬性標示的欄位會序列化。  然而，在還原序列化時會忽略欄位，而且這個欄位會保留與型別相關聯的預設值。  還原序列化事件處理常式應該宣告為在還原序列化處理期間設定欄位。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將還原序列化事件處理方法加入至型別。  
  
## 隱藏警告的時機  
 如果在還原序列化處理期間應該忽略欄位，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例會顯示含選擇性欄位的型別和還原序列化事件處理方法。  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## 相關規則  
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240：必須正確實作 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：請實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：請正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237：必須以 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120：必須保護序列化建構函式](../Topic/CA2120:%20Secure%20serialization%20constructors.md)