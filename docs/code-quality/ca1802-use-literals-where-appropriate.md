---
title: "CA1802：建議在適當時使用常值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1802：建議在適當時使用常值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 欄位宣告為 `static` 和 `readonly` \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 `Shared` and `ReadOnly`\)，並以編譯時期能計算的值進行初始化。  
  
## 規則描述  
 呼叫宣告型別的靜態建構函式 \(Constructor\) 時，`static` `readonly` 欄位的值會在執行階段進行計算。  如果 `static` `readonly` 欄位會在宣告時進行初始化，但卻未明確地宣告靜態建構函式，則編譯器會發出一個靜態建構函式以初始化欄位。  
  
 `const` 欄位的值會在編譯時期進行計算，並儲存於中繼資料 \(Metadata\) 中，在與 `static` `readonly` 欄位進行比較時，會增加執行階段的效能。  
  
 因為指定給目標欄位的值可在編譯時期進行計算，所以將宣告變更為 `const` 欄位，其值便可於編譯時期進行計算，而不是在執行階段計算。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請以 `const` 修飾詞 \(Modifier\) 來取代 `static` 和 `readonly` 修飾詞。  
  
## 隱藏警告的時機  
 如果效能並非考量重點，則您可以放心地隱藏這項規則的警告，或是停用該規則。  
  
## 範例  
 下列範例會顯示違反規則的型別 \(`UseReadOnly`\) 和符合規則的型別 \(`UseConstant`\)。  
  
 [!CODE [FxCop.Performance.UseLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals#1)]