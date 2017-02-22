---
title: "CA2238：請正確實作序列化方法 | Microsoft Docs"
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
  - "ImplementSerializationMethodsCorrectly"
  - "CA2238"
helpviewer_keywords: 
  - "CA2238"
  - "ImplementSerializationMethodsCorrectly"
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2238：請正確實作序列化方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|分類|Microsoft.Usage|  
|中斷變更|中斷 \- 如果可以在組件 \(Assembly\) 外部看見方法。<br /><br /> 非中斷 \- 如果不能在組件外部看見方法。|  
  
## 原因  
 處理序列化事件的方法沒有正確的簽章、傳回型別或可視性。  
  
## 規則描述  
 套用下列其中一個序列化事件屬性 \(Attribute\)，即可將序列化事件處理常式指定給方法：  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
 序列化事件處理常式會採用型別 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 的單一參數、傳回 `void`，以及具有 `private` 可視性。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請更正序列化事件處理常式的簽章、傳回型別或可視性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例顯示正確宣告的序列化事件處理常式。  
  
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-cs[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]  
  
## 相關規則  
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240：必須正確實作 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：請實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237：必須以 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120：必須保護序列化建構函式](../Topic/CA2120:%20Secure%20serialization%20constructors.md)