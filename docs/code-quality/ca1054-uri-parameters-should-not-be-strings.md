---
title: "CA1054：URI 參數不應該為字串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1054：URI 參數不應該為字串
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UriParametersShouldNotBeStrings|  
|CheckId|CA1054|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 型別會以名稱中包含 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url" 的字串參數宣告方法，並且型別不會宣告採用 <xref:System.Uri?displayProperty=fullName> 參數的對應多載。  
  
## 規則描述  
 這項規則會根據 Camel 命名法的大小寫慣例將參數名稱分割成語彙基元 \(Token\)，並檢查每個語彙基元是否等於 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。  如果有符合的項目，規則就會假設參數代表統一資源識別元 \(URI\)。  URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。  如果方法使用 URI 字串表示，應該提供採用 <xref:System.Uri> 類別的對應多載，這樣就可以透過安全的方式提供這些服務。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將參數變更為 <xref:System.Uri> 型別，而這會是中斷變更。  此外，也提供使用 <xref:System.Uri> 參數的方法多載，而這會是非中斷變更。  
  
## 隱藏警告的時機  
 如果參數不代表 URI，則您可以放心地隱藏此規則的警告。  
  
## 範例  
 下列程式碼範例會示範違反此規則的型別 \(`ErrorProne`\)，和滿足此規則的型別 \(`SaferWay`\)。  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## 相關規則  
 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234：必須傳遞 System.Uri 物件，而不要傳遞字串](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057：字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)