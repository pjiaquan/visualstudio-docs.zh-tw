---
title: "CA1055：URI 傳回值不應該為字串 | Microsoft Docs"
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
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1055：URI 傳回值不應該為字串
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UriReturnValuesShouldNotBeStrings|  
|CheckId|CA1055|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 方法名稱包含 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"，而且方法會傳回字串。  
  
## 規則描述  
 這項規則會將方法名稱分割成以 Pascal 命名法的大小寫慣例為基礎的語彙基元 \(Token\)，並檢查每一個語彙基元是否等於 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。  如果相符，規則即假設方法會傳回統一資源識別元 \(URI\)。  URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。  <xref:System.Uri?displayProperty=fullName> 類別以安全的方式提供這些服務。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將傳回型別變更為 <xref:System.Uri>。  
  
## 隱藏警告的時機  
 如果傳回值不代表 URI，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列程式碼範例會示範違反此規則的型別 \(`ErrorProne`\)，和滿足此規則的型別 \(`SaferWay`\)。  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]  
  
## 相關規則  
 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA2234：必須傳遞 System.Uri 物件，而不要傳遞字串](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057：字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)