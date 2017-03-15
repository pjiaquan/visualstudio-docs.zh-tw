---
title: "CA1018：以 AttributeUsageAttribute 標記屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018：以 AttributeUsageAttribute 標記屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> 屬性未出現於自訂屬性中。  
  
## 規則描述  
 定義自訂屬性時，請使用 <xref:System.AttributeUsageAttribute> 標示它，以指出可以在原始程式碼的哪個位置套用自訂屬性。  屬性的意義和預期的用法將決定它在程式碼中的有效位置。  例如，您可能定義屬性，用來識別誰負責維護和增強程式庫中的每個型別，以及確保永遠在型別層級指派責任。  在這種情況下，編譯器應該在類別、列舉和介面上啟用屬性 \(Attribute\)，但不應該在方法、事件或屬性 \(Property\) 上啟用它。  組織原則和程序將指出是否應該啟用組件 \(Assembly\) 上的屬性。  
  
 <xref:System.AttributeTargets?displayProperty=fullName> 列舉會定義您可以指定給自訂屬性的目標。  如果您省略 <xref:System.AttributeUsageAttribute>，自訂的屬性將會適用於 <xref:System.AttributeTargets> 列舉的 `All` 值所定義所有目標。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請使用 <xref:System.AttributeUsageAttribute> 指定屬性的目標。  請參閱下列範例。  
  
## 隱藏警告的時機  
 您應該修正此規則的違規情形，而不是排除訊息。  即使屬性繼承 <xref:System.AttributeUsageAttribute>，該屬性也應該出現以簡化程式碼維護。  
  
## 範例  
 下列範例會定義兩個屬性。  `BadCodeMaintainerAttribute` 不正確地省略 <xref:System.AttributeUsageAttribute> 陳述式，而 `GoodCodeMaintainerAttribute` 正確實作本節稍早說明的屬性。  請注意，[CA1019：必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)設計規則需要屬性 `DeveloperName`，且包括這個屬性後才比較完整。  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## 相關規則  
 [CA1019：必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813：避免使用非密封屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## 請參閱  
 [屬性](../Topic/Attributes1.md)