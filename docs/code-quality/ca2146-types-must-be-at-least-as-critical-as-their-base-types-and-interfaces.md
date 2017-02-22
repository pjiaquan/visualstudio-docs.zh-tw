---
title: "CA2146：類型至少必須和基底類型與介面一樣關鍵 | Microsoft Docs"
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
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2146：類型至少必須和基底類型與介面一樣關鍵
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 透明型別衍生自標記 <xref:System.Security.SecuritySafeCriticalAttribute> 或 <xref:System.Security.SecurityCriticalAttribute> 的型別，或者標記 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性的型別衍生自標記 <xref:System.Security.SecurityCriticalAttribute> 屬性的型別。  
  
## 規則描述  
 當衍生型別有安全性透明屬性，且該屬性的重要性不如基底型別或已實作之介面時，就會引發這個規則。  只有關鍵型別可以衍生自關鍵基底型別或實作關鍵介面，而且只有關鍵或安全關鍵型別可以衍生自安全關鍵基底型別或實作安全關鍵介面。  在層級 2 透明度違反此規則會導致衍生型別的 <xref:System.TypeLoadException>。  
  
## 如何修正違規  
 若要修正此違規情形，請標記衍生型別，或者實作具有透明屬性的型別，且該型別的重要性至少要和基底型別或介面一樣。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 [!CODE [FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes#1)]