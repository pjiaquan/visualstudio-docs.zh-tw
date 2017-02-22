---
title: "CA1027：必須以 FlagsAttribute 標記列舉 | Microsoft Docs"
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
  - "MarkEnumsWithFlags"
  - "CA1027"
helpviewer_keywords: 
  - "CA1027"
  - "MarkEnumsWithFlags"
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1027：必須以 FlagsAttribute 標記列舉
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用列舉的值是二的次方或在列舉中定義之其他值的組合，而且沒有 <xref:System.FlagsAttribute?displayProperty=fullName> 屬性 \(Attribute\)。  為了要減少誤報情形，此規則不會針對具有連續值的列舉報告違規。  
  
## 規則描述  
 列舉型別是一種實值型別 \(Value Type\)，用以定義一組相關的具名常數。  當列舉型別的具名常數可以有意義地加以結合時，會將 <xref:System.FlagsAttribute> 套用至此列舉型別。  例如，在追蹤哪一天資源可用的應用程式中，考慮星期天數的列舉。  如果每個資源的可用性都是使用具有 <xref:System.FlagsAttribute> 的列舉予以編碼，則可以代表任何天數組合。  沒有這個屬性，則只可表示星期的其中一天。  
  
 對於儲存可組合列舉的欄位而言，個別的列舉值會被視為欄位中的位元群組。  因此，此種欄位有時候就是指「*位元欄位*」\(Bit Field\)。  若要結合儲存在位元欄位中的列舉值，請使用布林 \(Boolean\) 條件運算子。  若要測試位元欄位，判斷特定列舉值是否存在，請使用布林邏輯運算子。  若要使用位元欄位正確儲存和擷取結合的列舉值，列舉中所定義的每個值都必須為二的次方。  除非情況如此，否則布林邏輯運算子就無法抽取欄位中所儲存的個別列舉值。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將 <xref:System.FlagsAttribute> 加入至列舉型別。  
  
## 隱藏警告的時機  
 如果您不想讓列舉值結合，請隱藏這項規則的警告。  
  
## 範例  
 在下列範例中，`DaysEnumNeedsFlags` 為符合使用 <xref:System.FlagsAttribute> 之需求的列舉型別 \(但並不具有此屬性\)。  `ColorEnumShouldNotHaveFlag` 列舉型別沒有為二的次方值，但卻錯誤地指定 <xref:System.FlagsAttribute>。  這會違反[CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)的規則。  
  
 [!CODE [FxCop.Design.EnumFlags#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags#1)]  
  
## 相關規則  
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## 請參閱  
 <xref:System.FlagsAttribute?displayProperty=fullName>