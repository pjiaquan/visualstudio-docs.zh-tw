---
title: "CA1800：請勿執行不必要的轉型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1800"
  - "DoNotCastUnnecessarily"
helpviewer_keywords: 
  - "DoNotCastUnnecessarily"
  - "CA1800"
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1800：請勿執行不必要的轉型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 方法對其中一個引數或區域變數執行重複轉型。  若要依此規則完整分析，則必須使用偵錯資訊建置測試的組件 \(Assembly\)，而且必須可以使用關聯的程式資料庫 \(.pdb\) 檔案。  
  
## 規則描述  
 重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。  若為明確重複轉型作業，請將轉型結果儲存在區域變數中，並改用區域變數而不用重複轉型作業。  
  
 如果 C\# `is` 運算子在執行實際轉型之前，用於測試轉型是否會成功，請考慮改為測試 `as` 運算子的結果。  這可提供相同的功能，而不需由 `is` 運算子執行隱含轉型作業。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請修改方法實作 \(Implementation\) 以最小化轉型作業的數目。  
  
## 隱藏警告的時機  
 如果效能並非考量重點，則您可以放心地隱藏這項規則的警告，或是完全忽略該規則。  
  
## 範例  
 下列範例會顯示使用 C\# `is` 運算子的方法違反規則。  第二個方法會滿足規則，做法是以 `as` 運算子的結果測試取代 `is` 運算子，而將每個反覆運算的轉型作業數目由兩個減少到一個。  
  
 [!code-cs[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## 範例  
 下列範例會顯示違反規則的方法 `start_Click` \(該方法具有多個重複明確轉型\)，以及滿足規則的方法 `reset_Click` \(該方法會將轉型儲存在區域變數中\)。  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-cs[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## 請參閱  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)