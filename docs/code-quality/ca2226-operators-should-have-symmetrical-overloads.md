---
title: "CA2226：運算子應該有對稱的多載 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorsShouldHaveSymmetricalOverloads"
  - "CA2226"
helpviewer_keywords: 
  - "CA2226"
  - "OperatorsShouldHaveSymmetricalOverloads"
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2226：運算子應該有對稱的多載
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 型別實作等號比較運算子或不等比較運算子，但未實作相反的運算子。  
  
## 規則描述  
 在所有情況下，只要等號比較運算子或不等比較運算子可以套用到型別的執行個體，就必須定義相反的運算子。  通常型別實作不等比較運算子的方式是傳回與等號比較運算子相反的值。  
  
 C\# 編譯器會產生違反此規則的錯誤。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請同時實作等號比較運算子和不等比較運算子，或移除現有的運算子。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  如果您的型別與 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 一致，就會無法運作。  
  
## 相關規則  
 [CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：運算子多載必須有具名的替代方法](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)