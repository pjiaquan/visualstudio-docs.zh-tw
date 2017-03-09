---
title: "CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode | Microsoft Docs"
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
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 public 型別會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName>，但不會覆寫 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>。  
  
## 規則描述  
 <xref:System.Object.GetHashCode%2A> 會依據目前執行個體 \(Instance\) 傳回值，適用於雜湊演算法和資料結構，如雜湊資料表。  兩個型別相同且相等的物件必須傳回相同的雜湊程式碼，才能確保下列型別的執行個體運作正常。  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   實作 <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName> 的型別  
  
## 如何修正違規  
 若要修正違反此規則的情形，請提供 <xref:System.Object.GetHashCode%2A> 的實作。  對於一組相同型別的物件，如果 <xref:System.Object.Equals%2A> 的實作會針對這組物件傳回 `true`，則您必須確定實作會傳回相同值。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 類別範例  
  
### 描述  
 下列範例顯示違反此規則的類別 \(參考型別\)。  
  
### 程式碼  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### 註解  
 下列範例藉由覆寫 <xref:System.Object.GetHashCode> 修正違規。  
  
### 程式碼  
 [!CODE [FxCop.Usage.GetHashCodeFixedClass#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass#1)]  
  
## 結構範例  
  
### 描述  
 下列範例顯示違反此規則的結構 \(實值型別\)。  
  
### 程式碼  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
### 註解  
 下列範例藉由覆寫 <xref:System.Object.GetHashCode> 修正違規。  
  
### 程式碼  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
## 相關規則  
 [CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：運算子多載必須有具名的替代方法](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## 請參閱  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [等號比較運算子](../Topic/Equality%20Operators.md)