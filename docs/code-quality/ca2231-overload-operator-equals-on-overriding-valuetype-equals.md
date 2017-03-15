---
title: "CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子 | Microsoft Docs"
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
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 實值型別 \(Value Type\) 會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName>，但並未實作等號比較運算子。  
  
## 規則描述  
 在大部分程式語言中沒有實值型別的等號比較運算子 \(\=\=\) 的預設實作。  如果您的程式語言支援運算子多載，您應該考慮實作等號比較運算子。  它的行為應該與 <xref:System.Object.Equals%2A> 的行為完全相同。  
  
 您無法在等號比較運算子的多載實作中，使用預設的等號比較運算子，  這樣做會導致堆疊溢位 \(Stack Overflow\)。  若要實作等號比較運算子，請在實作中使用 Object.Equals 方法。  例如：  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## 如何修正違規  
 若要修正此規則的違規情形，請實作等號比較運算子。  
  
## 隱藏警告的時機  
 您可以放心地隱藏這項規則的警告。不過，建議您盡可能提供等號比較運算子。  
  
## 範例  
 下列範例定義違反此規則的型別。  
  
 [!CODE [FxCop.Usage.EqualsGetHashCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode#1)]  
  
## 相關規則  
 [CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：運算子多載必須有具名的替代方法](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## 請參閱  
 <xref:System.Object.Equals%2A?displayProperty=fullName>