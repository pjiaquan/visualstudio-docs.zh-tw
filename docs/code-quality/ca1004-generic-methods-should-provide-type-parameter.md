---
title: "CA1004：泛型方法應該提供類型參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1004：泛型方法應該提供類型參數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見之泛型方法的參數簽章不包含對應到此方法之所有型別參數的型別。  
  
## 規則描述  
 推斷是指如何利用傳遞到泛型方法的引數型別，而不是利用型別引數的明確規格，來決定泛型方法的型別引數。  若要啟用推斷，泛型方法的參數簽章必須包含與方法之型別參數具有相同型別的參數。  在上述情形中，不必指定型別引數。  使用所有型別參數的推斷時，呼叫泛型和非泛型執行個體方法 \(Instance Method\) 之語法是相同的。  這會簡化泛型方法的可用性。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請變更設計，讓參數簽章包含與方法之每個型別參數相同的型別參數。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  使用易於了解和使用的語法提供泛型，以便減少學習所需的時間，並增加新程式庫的採用率。  
  
## 範例  
 下列範例會顯示呼叫兩個泛型方法的語法。  `InferredTypeArgument` 的型別引數是推斷的，而 `NotInferredTypeArgument` 的型別引數則必須明確指定。  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## 相關規則  
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公開泛型清單](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)