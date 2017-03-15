---
title: "CA1036：必須在 Comparable 類型中覆寫方法 | Microsoft Docs"
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
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036：必須在 Comparable 類型中覆寫方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別會實作 <xref:System.IComparable?displayProperty=fullName> 介面，而且未覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName>，或未多載等號比較、不等比較、小於比較或大於比較的語言特定運算子。  如果型別只繼承介面的實作，此規則就不會報告違規。  
  
## 規則描述  
 定義自訂排序次序的型別會實作 <xref:System.IComparable> 介面。  <xref:System.IComparable.CompareTo%2A> 方法會傳回整數值，表示兩個型別執行個體的正確排序次序。  此規則會識別設定排序次序的型別。這表示不套用等號比較、不等比較、小於比較或大於比較的一般意義。  當您提供 <xref:System.IComparable> 的實作時，通常還必須覆寫 <xref:System.Object.Equals%2A>，以便傳回與 <xref:System.IComparable.CompareTo%2A> 一致的值。  如果您會覆寫 <xref:System.Object.Equals%2A>，而且是以支援運算子多載的語言進行編碼，則必須同時提供與 <xref:System.Object.Equals%2A> 一致的運算子。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請覆寫 <xref:System.Object.Equals%2A>。  如果您的程式語言可支援運算子多載，請提供下列運算子：  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 在 C\# 中，用於代表這些運算子的語彙基元如下所示：\=\=、\!\=、\< 和 \>。  
  
## 隱藏警告的時機  
 在 Visual Basic .NET 中，當違規原因為遺失運算子且程式語言不支援運算子多載時，您就可以放心地隱藏這項規則的警告。  如果您判斷在應用程式內容中實作運算子不具意義，當這項規則的警告會在 op\_Equality 以外的等號比較運算子上引發時，隱藏該警告也是安全的。  但是，如果您覆寫 Object.Equals，就永遠都要覆寫 op\_Equality 和 \=\= 運算子。  
  
## 範例  
 下列範例會包含正確實作 <xref:System.IComparable> 的型別。  程式碼註解會識別滿足與 <xref:System.Object.Equals%2A> 和 <xref:System.IComparable> 介面相關之各種規則的方法。  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## 範例  
 下列應用程式會測試先前所示之 <xref:System.IComparable> 實作的行為。  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## 請參閱  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [等號比較運算子](../Topic/Equality%20Operators.md)