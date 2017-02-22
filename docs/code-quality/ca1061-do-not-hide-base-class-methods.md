---
title: "CA1061：不要隱藏基底類別方法 | Microsoft Docs"
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
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1061：不要隱藏基底類別方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 衍生型別 \(Derived Type\) 會宣告具相同名稱的方法，且其參數個數會與它其中一個基底 \(Base\) 方法的參數個數相同。其中的一或多個參數會是基底方法中對應參數的基底型別 \(Base Type\)，而剩餘的其他參數則會具有與基底方法中對應參數完全相同的型別。  
  
## 規則描述  
 只有在衍生方法的參數簽章因型別衍生時比基底方法參數簽章中的型別還要弱時，基底型別中的方法才會被衍生型別中的相同具名方法所隱藏。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除或重新命名此方法，或是變更參數簽章，因此方法不需隱藏基底方法。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反此規則的方法。  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]