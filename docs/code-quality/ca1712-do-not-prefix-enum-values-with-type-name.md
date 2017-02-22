---
title: "CA1712：不要使用類型名稱做為列舉值的前置字元 | Microsoft Docs"
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
  - "CA1712"
  - "DoNotPrefixEnumValuesWithTypeName"
helpviewer_keywords: 
  - "CA1712"
  - "DoNotPrefixEnumValuesWithTypeName"
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1712：不要使用類型名稱做為列舉值的前置字元
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotPrefixEnumValuesWithTypeName|  
|CheckId|CA1712|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 列舉 \(Enumeration\) 包含的成員名稱會以列舉的型別名稱做為開頭。  
  
## 規則描述  
 因為型別資訊必須由開發工具提供，所以列舉型別成員的名稱不能以型別名稱做為開頭。  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短學習新軟體程式庫的時間，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請從列舉型別成員移除型別名稱或前置字元。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 在下列範例中，程式碼會顯示命名錯誤的列舉型別，後面跟著正確的版本。  
  
 [!code-cs[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]  
  
## 相關規則  
 [CA1711：識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## 請參閱  
 <xref:System.Enum?displayProperty=fullName>