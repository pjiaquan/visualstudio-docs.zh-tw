---
title: "Option Strict 為 On 時，不可進行 &#39;&lt;類型1&gt;&#39; 至 &#39;&lt;類型2&gt;&#39; 的隱含轉換。Visual Basic 6.0 集合類型與 .NET Framework 集合類型不相容 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30753"
  - "bc30753"
helpviewer_keywords: 
  - "BC30753"
ms.assetid: 7e1bb22e-a507-483e-bfd6-f3a43e24a232
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict 為 On 時，不可進行 &#39;&lt;類型1&gt;&#39; 至 &#39;&lt;類型2&gt;&#39; 的隱含轉換。Visual Basic 6.0 集合類型與 .NET Framework 集合類型不相容
`Option Strict On` 時，不可進行 '`<type1>`' 至 '`<type2>`' 的隱含轉換。Visual Basic 6.0 集合類型與 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 集合類型不相容。  
  
 Visual Basic 6.0 中使用的集合物件與 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 中使用的集合物件不同。  
  
 **錯誤 ID︰**BC30753  
  
### 更正這個錯誤  
  
-   請使用其中一個類型轉換關鍵字，明確轉換集合物件。 如果轉換失敗，[CType 函式](/dotnet/visual-basic/language-reference/functions/ctype-function) 和 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator) 關鍵字會擲回執行階段例外狀況。 如果轉換失敗，[TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator) 關鍵字會傳回 [Nothing](/dotnet/visual-basic/language-reference/nothing)。  
  
## 請參閱  
 [CType 函式](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [NIB: Visual Basic 中的集合](http://msdn.microsoft.com/zh-tw/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)