---
title: "CA1005：避免在泛型類型上包含過多參數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1005：避免在泛型類型上包含過多參數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的泛型型別具有兩個以上的型別參數。  
  
## 規則描述  
 泛型型別所包含的型別參數越多，就越難了解並記住每個型別參數所代表的含意。  若是只包含一種型別參數 \(如 `List<T>`\)，以及包含兩個型別參數的某些特定情況 \(如 `Dictionary<TKey, TValue>`\)，這些通常都清楚易懂。  如果有兩個以上的型別參數存在，則對大多數使用者而言都會變得難以理解 \(例如 C\# 中的 `TooManyTypeParameters<T, K, V>` 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 的 `TooManyTypeParameters(Of T, K, V)`\)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將設計變更為只使用兩個以下的型別參數。  
  
## 隱藏警告的時機  
 除非設計上絕對需要兩個以上的型別參數，否則請勿隱藏此規則的警告。  使用易於了解和使用的語法提供泛型，以便減少學習所需的時間，並增加新程式庫的採用率。  
  
## 相關規則  
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公開泛型清單](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)