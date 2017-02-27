---
title: "CA1047：不要在密封類型中宣告 protected 成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1047：不要在密封類型中宣告 protected 成員
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用 \(Public\) 型別為 `sealed` \(在 Visual Basic 中則為 `NotInheritable`\)，而且會宣告 Protected 成員或 Protected 巢狀型別。  這項規則不會報告 <xref:System.Object.Finalize%2A> 方法的違規情形，這些方法必須遵循此模式。  
  
## 規則描述  
 型別會宣告 protected 成員，如此繼承的型別即可存取或覆寫成員。  在定義中可以得知，您無法繼承自密封型別，這表示無法呼叫密封型別上的 Protected 方法。  
  
 C\# 編譯器會針對這個錯誤發出警告。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將成員的存取層級變更為 Private，或者讓型別變成可以繼承。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  使型別保持它的目前狀態可能會造成維護問題，而且不會提供任何好處。  
  
## 範例  
 下列範例顯示違反此規則的型別。  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]