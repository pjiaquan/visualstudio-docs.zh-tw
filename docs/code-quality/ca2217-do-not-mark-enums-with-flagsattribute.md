---
title: "CA2217：不要以 FlagsAttribute 標記列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotMarkEnumsWithFlags"
  - "CA2217"
helpviewer_keywords: 
  - "CA2217"
  - "DoNotMarkEnumsWithFlags"
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2217：不要以 FlagsAttribute 標記列舉
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 從外部可見的列舉會以 <xref:System.FlagsAttribute> 標記，並且有一個或多個不是二的次方，或組合列舉上其他定義值之次方的值。  
  
## 規則描述  
 只有當列舉型別中定義的每個值都是二的次方或已定義值的組合時，列舉型別中才會有 <xref:System.FlagsAttribute> 存在。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請從列舉型別中移除 <xref:System.FlagsAttribute>。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會示範其中包含值 3 的 Color 列舉，這個列舉不是二的次方，也不是組合任何定義值的次方。  Color 列舉不應該以 <xref:System.FlagsAttribute> 標記。  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## 範例  
 下列範例會示範符合以 System.FlagsAttribute 標記之需求的 Days 列舉。  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## 相關規則  
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## 請參閱  
 <xref:System.FlagsAttribute?displayProperty=fullName>