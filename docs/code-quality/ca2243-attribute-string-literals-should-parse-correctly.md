---
title: "CA2243：屬性字串常值必須正確剖析 | Microsoft Docs"
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
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2243：屬性字串常值必須正確剖析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 屬性 \(Attribute\) 的字串常值 \(String Literal\) 未針對 URL、GUID 或版本進行正確剖析。  
  
## 規則描述  
 由於屬性都是衍生自 <xref:System.Attribute?displayProperty=fullName>，而且會在編譯時期使用，因此只能將常數值傳遞到屬性的建構函式 \(Constructor\)。  必須表示 URL、GUID 和版本的屬性參數不能是 <xref:System.Uri?displayProperty=fullName>、<xref:System.Guid?displayProperty=fullName> 和 <xref:System.Version?displayProperty=fullName> 型別，因為這些型別不能以常數表示。  而必須用字串來表示。  
  
 由於參數的型別為字串，因此在編譯時期可能會傳遞格式不正確的參數。  
  
 此規則使用命名啟發學習法 \(Heuristic\) 找出代表統一資源識別項 \(URI\)、全域唯一識別項 \(GUID\) 或版本的參數，並驗證傳遞值是否正確。  
  
## 如何修正違規  
 將參數字串改成正確格式的 URL、GUID 或版本。  
  
## 隱藏警告的時機  
 如果參數不代表 URL、GUID 或版本，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例顯示違反此規則之 AssemblyFileVersionAttribute 的程式碼。  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 此規則由下列項目觸發：  
  
-   包含 ‘version’ 而且無法剖析為 System.Version 的參數。  
  
-   包含 ‘guid’ 而且無法剖析為 System.Guid 的參數。  
  
-   包含 ‘uri’、'urn' 或 ‘url’ 而且無法剖析為 System.Uri 的參數。  
  
## 請參閱  
 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)