---
title: "CA1501：避免過度繼承 | Microsoft Docs"
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
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1501：避免過度繼承
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|分類|Microsoft.Maintainability|  
|中斷變更|中斷|  
  
## 原因  
 型別在其繼承階層架構 \(Inheritance Hierarchy\) 中超過四個層級的深度。  
  
## 規則描述  
 太深的巢狀型別階層架構可能會難以依循、了解和維護。  這項規則會使階層架構的分析限制在相同的模組內。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請從繼承階層架構中較淺的基底型別 \(Base Type\) 衍生型別，或排除某些中繼基底型別。  
  
## 隱藏警告的時機  
 您可以放心地隱藏這項規則的警告。  不過，程式碼可能會更難維護。  請注意，視基底型別的可視性而定，解決這項規則的違規情形可能會產生中斷變更。  例如，移除公用基底型別為中斷變更。  
  
## 範例  
 下列範例顯示違反規則的型別。  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]