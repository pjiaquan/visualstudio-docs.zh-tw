---
title: "CA1006：不要在成員簽章中巢狀化泛型類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1006：不要在成員簽章中巢狀化泛型類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見成員具有內含巢狀型別 \(Nested Type\) 引數的簽章。  
  
## 規則描述  
 巢狀型別引數就是也是泛型型別的型別引數。  若要呼叫其簽章含有巢狀型別引數的成員，則使用者必須具現化 \(Instantiate\) 一個泛型型別，並將這個型別傳遞給第二個泛型型別的建構函式。  必要程序及語法十分複雜，且應予以避免。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將設計變更成移除巢狀型別引數。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  使用易於了解和使用的語法提供泛型，以便減少學習所需的時間，並增加新程式庫的採用率。  
  
## 範例  
 下列範例顯示違反規則的方法，以及呼叫違規方法所需的語法。  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## 相關規則  
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公開泛型清單](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)