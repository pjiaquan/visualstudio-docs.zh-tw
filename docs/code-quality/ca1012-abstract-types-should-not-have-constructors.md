---
title: "CA1012：抽象類型不應具有建構函式 | Microsoft Docs"
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
  - "AbstractTypesShouldNotHaveConstructors"
  - "CA1012"
helpviewer_keywords: 
  - "CA1012"
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1012：抽象類型不應具有建構函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用 \(Public\) 型別為抽象的且具有公用建構函式。  
  
## 規則描述  
 只有衍生型別 \(Derived Type\) 可以呼叫抽象型別上的建構函式。  因為公用建構函式會建立型別的執行個體，而且您無法建立抽象型別的執行個體，因此具有公用建構函式的抽象型別設計不正確。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請使建構函式受到保護，或者勿將型別宣告為抽象。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  抽象型別具有公用建構函式。  
  
## 範例  
 下列範例包含違反此規則的抽象型別。  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-cs[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## 範例  
 下列範例透過將建構函式的存取範圍從 `public` 改成 `protected`，以修正前述的違規情形。  
  
 [!code-cs[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]