---
title: "CA1715：識別項名稱應該使用正確的前置字元 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1715：識別項名稱應該使用正確的前置字元
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|分類|Microsoft.Naming|  
|中斷變更|中斷 \- 對介面引發時<br /><br /> 非中斷 \- 在泛型型別參數上引發時。|  
  
## 原因  
 外部可見介面的名稱沒有以大寫 'I' 開頭。  
  
 \-或\-  
  
 外部可見型別或方法上泛型型別參數的名稱沒有以大寫 'T' 開頭。  
  
## 規則描述  
 根據慣例，特定程式設計項目的名稱會以特定的前置字元做為開頭。  
  
 介面名稱必須以大寫的 'I' 做為開頭，後面跟著另一個大寫字母。  此規則會報告違規的介面名稱，例如 'MyInterface' 和 'IsolatedInterface'。  
  
 泛型型別參數名稱必須以大寫的 'T' 做為開頭，後面可以跟著另一個大寫字母。  這個規則會報告違規的泛型型別參數名稱，例如 'V' 和 'Type'。  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短新軟體程式庫的學習過程，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 請將識別項重新命名為具有正確前置字元的名稱。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 **下列範例示範命名錯誤的介面。**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## 範例  
 **下列範例會在介面使用前置詞 'I' 修正先前的違規。**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## 範例  
 **下列範例示範命名錯誤的泛型型別參數。**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1)]  
  
## 範例  
 **下列範例會在泛型型別參數使用前置詞 'T' 修正先前的違規。**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1)]  
  
## 相關規則  
 [CA1722：識別項不應使用不正確的前置字元](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)