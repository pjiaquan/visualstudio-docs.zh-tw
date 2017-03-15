---
title: "CA2132：預設建構函式至少必須和基底類型的預設建構函式一樣關鍵 | Microsoft Docs"
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
  - "CA2132"
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2132：預設建構函式至少必須和基底類型的預設建構函式一樣關鍵
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
> [!NOTE]
>  這個警告只會套用至執行 CoreCLR \(專屬於 Silverlight Web 應用程式的 CLR 版本\) 的程式碼。  
  
## 原因  
 衍生類別之預設建構函式的透明度屬性重要性不如基底類別的透明度。  
  
## 規則描述  
 Silverlight 應用程式程式碼無法使用擁有 <xref:System.Security.SecurityCriticalAttribute> 的型別及成員。  重視安全性的型別以及成員，只能夠由 .NET Framework for Silverlight 類別庫中的受信任程式碼使用。  由於衍生類別中的公用或受保護建構所具有的透明度必須大於或等於其基底類別，因此應用程式中的類別不可衍生自標記為 SecurityCritical 的類別。  
  
 針對 CoreCLR 平台程式碼，如果基底型別具有公用或保護的非透明預設建構函式，則衍生型別必須遵守預設建構函式的繼承規則。  衍生型別也必須具有預設建構函式，而且該建構函式的重要性必須至少為基底型別的預設建構函式。  
  
## 如何修正違規  
 若要修正違規情形，請移除型別，或者不要從安全性不透明型別衍生。  
  
## 隱藏警告的時機  
 不隱藏此規則的警告。  應用程式程式碼違反這項規則會導致 CoreCLR 拒絕載入含有 <xref:System.TypeLoadException> 的型別。  
  
### 程式碼  
 [!CODE [FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency#1)]  
  
### 註解