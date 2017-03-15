---
title: "CA1034：巢狀類型不應為可見 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1034：巢狀類型不應為可見
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的型別包含外部可見的型別宣告 \(Type Declaration\)，  但是巢狀列舉和受保護的型別則不受限於此規則。  
  
## 規則描述  
 巢狀型別是在其他型別範圍內宣告的型別。  巢狀型別在封裝包含型別 \(Containing Type\) 私用的 \(Private\) 實作細節時相當有用。  因為有這樣的用途，所以巢狀型別不應為外部可見的。  
  
 請勿使用外部可見的巢狀型別進行邏輯群組或避免名稱衝突，請改用命名空間。  
  
 巢狀型別包含成員存取範圍的概念；某些程式設計人員並不十分清楚這個概念。  
  
 受保護的型別適用於進階自訂案例中的子類別和巢狀型別。  
  
## 如何修正違規  
 如果您不想讓巢狀型別變成外部可見，請變更型別的存取範圍。  否則，請從父代 \(Parent\) 移除巢狀型別。  如果巢狀結構的目的是將巢狀型別進行分類，請改用命名空間建立階層架構。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例顯示違反規則的型別。  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]