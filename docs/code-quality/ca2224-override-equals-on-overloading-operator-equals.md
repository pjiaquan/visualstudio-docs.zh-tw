---
title: "CA2224：多載等號比較運算子時必須一併覆寫 Equals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2224：多載等號比較運算子時必須一併覆寫 Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 public 型別會實作等號比較運算子，但不會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName>。  
  
## 規則描述  
 等號比較運算子主要是在語法上提供便利的使用方式，以存取 <xref:System.Object.Equals%2A> 方法的功能。  如果您實作等號比較運算子，則它的邏輯必須等於 <xref:System.Object.Equals%2A> 的邏輯。  
  
 如果程式碼違反這項規則，則 C\# 編譯器將會發出警告。  
  
## 如何修正違規  
 若要修正此規則的違規，您應該移除等號比較運算子的實作，或是覆寫 <xref:System.Object.Equals%2A> 並使這兩個方法傳回相同值。  如果等號比較運算子沒有引入不一致的行為，則您可以提供 <xref:System.Object.Equals%2A> 的實作，在基底類別中呼叫 <xref:System.Object.Equals%2A> 方法，以修正違規。  
  
## 隱藏警告的時機  
 如果等號比較運算子會傳回與 <xref:System.Object.Equals%2A> 之繼承實作相同的值，則您可以放心地隱藏對這項規則的警告。  範例中會包括可放心地隱藏這項規則之警告的型別。  
  
## 不一致等式定義範例  
  
### 描述  
 下列範例顯示等式定義不一致的型別。  `BadPoint` 藉由提供相等運算子的自訂實作，卻不覆寫 <xref:System.Object.Equals%2A> 而使其行為相同，進而變更了相等的意義。  
  
### 程式碼  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## 範例  
 下列程式碼會測試 `BadPoint` 的行為。  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 這個範例產生下列輸出。  
  
  **a \= \(\[0\] 1,1\) 和 b \= \(\[1\] 2,2\) 是否相等？**  
 **No a \=\= b?**  
 **No a1 和 a 相等?**  
 **Yes a1 \=\= a?**  
 **Yes b 和 bcopy 相等?**  
 **No b \=\= bcopy ?**  
 **是**   
## 範例  
 下列範例會顯示在技術上違反這項規則，但不會以不一致方式運作的型別。  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## 範例  
 下列程式碼會測試 `GoodPoint` 的行為。  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 這個範例產生下列輸出。  
  
  **a \= \(1,1\) 和 b \= \(2,2\) 是否相等？**  
 **No a \=\= b?**  
 **No a1 和 a 相等?**  
 **Yes a1 \=\= a?**  
 **Yes b 和 bcopy 相等?**  
 **Yes b \=\= bcopy?**  
 **是**   
## 類別範例  
  
### 描述  
 下列範例顯示違反此規則的類別 \(參考型別\)。  
  
### 程式碼  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## 範例  
 下列範例藉由覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName> 修正違規。  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## 結構範例  
  
### 描述  
 下列範例顯示違反此規則的結構 \(實值型別\)。  
  
### 程式碼  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## 範例  
 下列範例藉由覆寫 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 修正違規。  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## 相關規則  
 [CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：運算子多載必須有具名的替代方法](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)