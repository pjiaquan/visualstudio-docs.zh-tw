---
title: "CA1806：不要忽略方法的結果 | Microsoft Docs"
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
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806：不要忽略方法的結果
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 有許多的可能原因會導致發生這個警告：  
  
-   建立從未使用的新物件。  
  
-   呼叫建立與傳回新字串的方法，並且從未使用新字串。  
  
-   傳回從未使用之 HRESULT 或錯誤碼的 COM 或 P\/Invoke 方法。  規則描述  
  
 未使用之物件的不必要物件建立及關聯的記憶體回收會降低效能。  
  
 字串是不變的，且 String.ToUpper 這類方法會傳回字串的新執行個體，而非修改呼叫方法中字串的執行個體。  
  
 忽略 HRESULT 或錯誤碼，可能導致錯誤情況或資源不足情況的非預期行為。  
  
## 如何修正違規  
 如果方法 A 建立 B 物件的新執行個體，但是從未使用，請將執行個體當做引數傳遞至其他方法，或將執行個體指派至變數。  如果不需要建立物件，請移除它。\-或\-  
  
 如果方法 A 會呼叫方法 B，但不會使用方法 B 傳回的新字串執行個體，  請將執行個體當做引數傳遞至另一個方法，指派執行個體給變數，  或是移除呼叫 \(如果不需要的話\)。  
  
 \-或\-  
  
 如果方法 A 會呼叫方法 B，但是不會使用方法傳回的 HRESULT 或錯誤碼。  請在條件陳述式中使用結果、指派結果給變數，或將它當做引數傳遞給另一個方法。  
  
## 隱藏警告的時機  
 除非建立物件的動作是有其他目的，否則請勿隱藏此規則的警告。  
  
## 範例  
 下列範例顯示的類別，會忽略呼叫 String.Trim 的結果。  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## 範例  
 下列範例藉由將 String.Trim 的結果指派回進行呼叫之變數，修正上述違規。  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## 範例  
 下列範例示範不使用其建立之物件的方法。  
  
> [!NOTE]
>  在 Visual Basic 中無法重現這項違規。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## 範例  
 下列範例會藉由移除不必要的物件建立以修正上述違規。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## 範例  
 下列範例顯示的方法，會忽略原生方法 GetShortPathName 傳回的錯誤碼。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## 範例  
 下列範例會藉由檢查錯誤碼，並在呼叫失敗時擲回例外狀況，以修正上述違規。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]