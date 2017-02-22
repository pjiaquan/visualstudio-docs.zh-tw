---
title: "CA1820：應該使用字串長度測試空白字串 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1820：應該使用字串長度測試空白字串
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 使用 <xref:System.Object.Equals%2A?displayProperty=fullName> 比較字串與空字串。  
  
## 規則描述  
 使用 <xref:System.String.Length%2A?displayProperty=fullName> 屬性或 <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> 方法比較字串，明顯地會比使用 <xref:System.Object.Equals%2A> 還快。  這是因為 <xref:System.Object.Equals%2A> 所執行的 MSIL 指令數目，明顯地比 <xref:System.String.IsNullOrEmpty%2A>，或擷取 <xref:System.String.Length%2A> 屬性值再與零相比所執行的指令數目更多。  
  
 您應該注意 <xref:System.Object.Equals%2A> 和 <xref:System.String.Length%2A> \=\= 0 在處理 null 字串時有所不同。  如果您嘗試取得 null 字串的 <xref:System.String.Length%2A> 屬性值，則 Common Language Runtime 會擲回 <xref:System.NullReferenceException?displayProperty=fullName>。  如果您在 null 字串與空字串之間執行比較，則 Common Language Runtime 並不會擲回例外狀況 \(Exception\)，而是傳回 `false`。  進行 null 測試並不會明顯影響這兩種方法的相對效能。  以 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 為目標時，請使用 <xref:System.String.IsNullOrEmpty%2A> 方法。  否則，請盡量使用 <xref:System.String.Length%2A> \=\= 比較。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將比較變更為使用 <xref:System.String.Length%2A> 屬性，並測試 null 字串。  以 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 為目標時，請使用 <xref:System.String.IsNullOrEmpty%2A> 方法。  
  
## 隱藏警告的時機  
 如果效能不是問題，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例會說明用以尋找空字串的不同技巧。  
  
 [!CODE [FxCop.Performance.StringTest#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest#1)]