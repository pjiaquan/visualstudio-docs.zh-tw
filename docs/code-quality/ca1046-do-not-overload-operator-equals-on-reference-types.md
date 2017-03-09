---
title: "CA1046：請勿多載參考類型上的等號比較運算子 | Microsoft Docs"
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
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046：請勿多載參考類型上的等號比較運算子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 public 參考型別或巢狀的 Public 參考型別會多載等號比較運算子。  
  
## 規則描述  
 對參考型別而言，等號比較運算子的預設實作 \(Implementation\) 永遠都是正確的。  根據預設，只有當兩項參考都指向相同物件時才會相等。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除等號比較運算子的實作。  
  
## 隱藏警告的時機  
 如果參考型別的作用如同內建實值型別 \(Value Type\)，則您可以放心地隱藏這項規則的警告。  如果在該型別的執行個體 \(Instance\) 上進行加法或減法是有意義的，則實作等號比較運算子並隱藏違規可能是正確做法。  
  
## 範例  
 以下為比較兩個參考時之預設行為的範例。  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## 範例  
 下列應用程式會比較某些參考。  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 這個範例產生下列輸出。  
  
  **a \= new \(2,2\) 和 b \= new \(2,2\) 是否相等？**  
 **c 和 a不相等?**  
 **b 和 a為\=\=?**  
 **c 和 a不是\=\=?**  
 **是**   
## 相關規則  
 [CA1013：多載加號和減號運算子時必須一併多載等號比較運算子](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## 請參閱  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [等號比較運算子](../Topic/Equality%20Operators.md)