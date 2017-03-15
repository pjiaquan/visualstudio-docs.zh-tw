---
title: "CA2104：不要宣告唯讀的可變動參考類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2104：不要宣告唯讀的可變動參考類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 外部可見型別包含了可變動參考型別的外部可見唯讀欄位。  
  
## 規則描述  
 可變動型別是可以修改執行個體 \(Instance\) 資料的型別。  <xref:System.Text.StringBuilder?displayProperty=fullName> 類別 \(Class\) 則是可變動參考型別的範例。  其中包含的成員可以變更類別執行個體的值。  不可變動參考型別的範例則為 <xref:System.String?displayProperty=fullName> 類別。  執行個體化類別之後，該類別的值就不會再變更。  
  
 參考型別欄位 \(C\+\+ 中的指標\) 上的唯讀修飾詞 \(Modifier\) \(在 C\# 中是 [readonly](/dotnet/csharp/language-reference/keywords/readonly)、在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中是 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)，而在 C\+\+ 中是 [const](/visual-cpp/cpp/const-cpp)\) 會防止由不同的參考型別執行個體取代欄位。  但是，修飾詞無法防止欄位的執行個體資料經由參考型別遭到修改。  
  
 唯讀陣列欄位不受限於此規則，不過會導致發生[CA2105：陣列欄位不應為唯讀](../code-quality/ca2105-array-fields-should-not-be-read-only.md)規則的違規情形。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除唯讀修飾詞或使用不可變動的型別取代欄位 \(如果可接受中斷變更\)。  
  
## 隱藏警告的時機  
 如果欄位型別為不可變動，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例顯示導致違反此規則之情形的欄位宣告。  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]