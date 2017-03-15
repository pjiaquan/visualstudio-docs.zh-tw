---
title: "CA1013：多載加號和減號運算子時必須一併多載等號比較運算子 | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013：多載加號和減號運算子時必須一併多載等號比較運算子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別會實作加法或減法運算，但不會實作等號比較運算子。  
  
## 規則描述  
 使用如加法和減法的運算將型別的執行個體 \(Instance\) 加以組合時，您應該都會定義等號比較，以針對任兩個具有相同構成值的執行個體傳回 `true`。  
  
 您無法在等號比較運算子的多載實作中，使用預設的等號比較運算子，  這樣做會導致堆疊溢位 \(Stack Overflow\)。  若要實作等號比較運算子，請在實作中使用 Object.Equals 方法。  請參閱下列範例。  
  
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
 若要修正此規則的違規情形，請實作等號比較運算子，讓它在算術上會與加法和減法運算子一致。  
  
## 隱藏警告的時機  
 當等號比較運算子的預設實作會提供型別的正確行為時，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例會定義違反這項規則的型別 \(`BadAddableType`\)。  這個型別應該會實作等號比較運算子，以便在任兩個具有相同欄位值的執行個體相等時，使它的測試結果為 `true`。  型別 `GoodAddableType` 會顯示已更正的實作。  請注意，這個型別也會實作不等比較運算子並覆寫 <xref:System.Object.Equals%2A> 以滿足其他規則。  完整實作也會實作 <xref:System.Object.GetHashCode%2A>。  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## 範例  
 下列範例會使用本主題先前所定義的型別執行個體測試是否相等，以說明等號比較運算子的預設行為和正確行為。  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 這個範例產生下列輸出。  
  
  **錯誤的型別：{2,2} {2,2} 是否相等？  沒有**  
**良好型別：{3,3} {3,3} 是否相等？  有**  
**良好型別：{3,3} {3,3} 是否 \=\=？有**  
**錯誤的型別：{2,2} {9,9} 是否相等？  沒有**  
**良好型別：{3,3} {9,9} 是否 \=\=？沒有**    
## 請參閱  
 [等號比較運算子](../Topic/Equality%20Operators.md)