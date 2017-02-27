---
title: "CA2242：必須正確測試 NaN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2242：必須正確測試 NaN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TestForNaNCorrectly|  
|CheckId|CA2242|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 運算式針對 <xref:System.Single.Nan?displayProperty=fullName> 或 <xref:System.Double.Nan?displayProperty=fullName> 測試值。  
  
## 規則描述  
 若未定義數學運算，將會傳回代表不是數字的 <xref:System.Double.NaN?displayProperty=fullName>。  任何測試值和 <xref:System.Double.NaN?displayProperty=fullName> 兩者是否相等的運算式都會傳回 `false`。  任何測試值和 <xref:System.Double.NaN?displayProperty=fullName> 兩者是否不相等的運算式則一定會傳回 `true`。  
  
## 如何修正違規  
 若要修正此規則的違規情形，並正確判斷值是否代表 <xref:System.Double.NaN?displayProperty=fullName>，請使用 <xref:System.Single.IsNan%2A?displayProperty=fullName> 或 <xref:System.Double.IsNan%2A?displayProperty=fullName> 來測試值。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例顯示兩個未正確依據 <xref:System.Double.NaN?displayProperty=fullName> 來測試值的運算式，以及一個正確使用 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 來測試值的運算式。  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]