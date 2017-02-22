---
title: "CA1707：識別項不應包含底線 | Microsoft Docs"
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
  - "IdentifiersShouldNotContainUnderscores"
  - "CA1707"
helpviewer_keywords: 
  - "CA1707"
  - "IdentifiersShouldNotContainUnderscores"
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1707：識別項不應包含底線
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|分類|Microsoft.Naming|  
|中斷變更|中斷 \- 在組件上引發時<br /><br /> 非中斷 \- 在型別參數上引發時|  
  
## 原因  
 識別項的名稱包含底線 \(\_\) 字元。  
  
## 規則描述  
 根據慣例，識別項名稱不包含底線 \(\_\) 字元。  規則會檢查命名空間、型別、成員和參數。  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短新軟體程式庫的學習過程，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 從名稱中移除所有底線字元。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 相關規則  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)