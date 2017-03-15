---
title: "CA1057：字串 URI 多載呼叫 System.Uri 多載 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057：字串 URI 多載呼叫 System.Uri 多載
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 型別所宣告的方法多載會因以 <xref:System.Uri?displayProperty=fullName> 參數取代字串參數而有所不同，但採用字串參數的多載不會呼叫採用 <xref:System.Uri> 參數的多載。  
  
## 規則描述  
 因為多載只有字串\/<xref:System.Uri> 參數的差異，因此會假設字串是表示統一資源識別元 \(URI\)。  URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。  <xref:System.Uri> 類別以安全的方式提供這些服務。  若要享有 <xref:System.Uri> 類別的優點，字串多載應該使用字串引數呼叫 <xref:System.Uri> 多載。  
  
## 如何修正違規  
 重新實作使用以字串表示之 URI 的方法，讓它能建立使用字串當做引數之 <xref:System.Uri> 類別的執行個體，再傳遞 <xref:System.Uri> 物件至具有 <xref:System.Uri> 參數的多載。  
  
## 隱藏警告的時機  
 如果字串參數不代表 URI，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 在下列範例中，程式碼會顯示正確實作的字串多載。  
  
 [!CODE [FxCop.Design.CallUriOverload#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload#1)]  
  
## 相關規則  
 [CA2234：必須傳遞 System.Uri 物件，而不要傳遞字串](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)