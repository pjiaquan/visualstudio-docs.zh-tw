---
title: "CA1007：建議在適當時使用泛型 | Microsoft Docs"
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
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1007：建議在適當時使用泛型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的方法會包含 <xref:System.Object?displayProperty=fullName> 型別的參考參數，而且包含的組件 \(Assembly\) 會以 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 為目標。  
  
## 規則描述  
 參考參數是使用 `ref` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `ByRef`\) 關鍵字所修改的參數。  提供給參考參數的引數型別 \(Argument Type\) 必須與參考參數型別完全相符。  若要使用衍生自參考參數型別的型別，則必須先轉型 \(Cast\) 該型別，並將之指派給參考參數型別的變數。  使用泛型方法可將所有型別 \(遵守條件約束\) 傳遞給方法，而不需要先將型別轉型為參考參數型別。  
  
## 如何修正違規  
 若要修正這個規則的違規情形，請將方法變成泛型，並使用型別參數取代 <xref:System.Object> 參數。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例顯示做為非泛型及泛型方法實作的一般用途交換常式。  請注意，與非泛型方法比較起來，使用泛型方法交換字串更加有效率。  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-cs[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## 相關規則  
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公開泛型清單](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
## 請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)