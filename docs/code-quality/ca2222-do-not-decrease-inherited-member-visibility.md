---
title: "CA2222：請勿降低繼承成員的可視性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2222：請勿降低繼承成員的可視性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 非密封型別之私用 \(Private\) 方法的簽章，與在基底型別 \(Base Type\) 中宣告的公用方法完全相同。  私用方法並非 Final。  
  
## 規則描述  
 您不得變更繼承成員的存取修飾詞 \(Modifier\)。  將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 \(Base Class\) 實作。  如果成員變成私用且型別為非密封，繼承型別可以呼叫在繼承階層架構 \(Inheritance Hierarchy\) 中方法的最後一個公用實作。  如果您必須變更存取修飾詞，則應該將方法標記為 Final 或是密封它的型別，以防止覆寫方法。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將存取變更為非私用。  此外，如果程式語言支援的話，您可以使方法成為 Final。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例顯示違反此規則的型別。  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]