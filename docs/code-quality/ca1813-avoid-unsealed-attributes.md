---
title: "CA1813：避免使用非密封屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813：避免使用非密封屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 繼承自 <xref:System.Attribute?displayProperty=fullName> 的 public 型別既非抽象的，亦非密封的 \(在 Visual Basic 中為 `NotInheritable`\)。  
  
## 規則描述  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Class Library 會提供擷取自訂屬性的方法。  根據預設，這些方法會搜尋屬性繼承階層架構 \(Inheritance Hierarchy\)，例如 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> 會搜尋指定的屬性型別，或搜尋任何會擴充指定之屬性型別的屬性型別。  密封屬性會減少對整個繼承階層架構的搜尋，並且可以改進效能。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請密封屬性型別或將它設為抽象。  
  
## 隱藏警告的時機  
 您可以放心地隱藏這項規則的警告。  但是您只能在定義屬性階層架構，卻無法密封屬性或將它設為抽象時，才能這麼做。  
  
## 範例  
 在下列範例中，程式碼會顯示滿足此規則的自訂屬性。  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## 相關規則  
 [CA1019：必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018：以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## 請參閱  
 [屬性](../Topic/Attributes1.md)