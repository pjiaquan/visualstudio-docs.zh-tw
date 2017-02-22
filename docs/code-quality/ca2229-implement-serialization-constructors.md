---
title: "CA2229：請實作序列化建構函式 | Microsoft Docs"
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
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2229：請實作序列化建構函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 型別實作 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面、不是委派 \(Delegate\) 或介面，並符合下列其中一個條件：  
  
-   型別沒有採用 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> 物件和 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 物件 \(序列化 \(Serialization\) 建構函式的簽章\) 的建構函式。  
  
-   型別為非密封且它的序列化建構函式的存取修飾詞 \(Modifier\) 不是 protected \(Family\)。  
  
-   型別為密封且它的序列化建構函式的存取修飾詞不是 private。  
  
## 規則描述  
 此規則會與支援自訂序列化的型別相關。  如果型別會實作 <xref:System.Runtime.Serialization.ISerializable> 介面，就表示會支援自訂序列化。  對於使用 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 方法序列化的物件，若要還原序列化或重新建立，則需要使用序列化建構函式。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請實作序列化建構函式。  針對密封類別，讓建構函式成為 private，否則為 protected。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的違規。  將該型別無法被還原序列化，而且在許多案例中也無法運作。  
  
## 範例  
 下列範例會顯示滿足規則的型別。  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## 相關規則  
 [CA2237：必須以 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## 請參閱  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>