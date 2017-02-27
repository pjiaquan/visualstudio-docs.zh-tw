---
title: "CA1721：屬性名稱不能和其中有 get 的方法名稱相符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1721：屬性名稱不能和其中有 get 的方法名稱相符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護之成員的名稱是以 'Get' 開頭，否則需符合公用或保護之屬性的名稱。  例如，包含名為 'GetColor' 的方法及名為 'Color' 的屬性的型別即違反這項規則。  
  
## 規則描述  
 Get 方法和屬性的名稱應該清楚區別其功能。  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短學習新軟體程式庫的時間，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 變更名稱，讓它不是以 'Get' 為字首的方法名稱。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
> [!NOTE]
>  如果是因為實作 IExtenderProvider 介面而導致 Get 方法，則可以排除這個警告。  
  
## 範例  
 下列範例會包含違反這項規則的方法和屬性。  
  
 [!CODE [FxCop.Naming.GetMethod#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod#1)]  
  
## 相關規則  
 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)