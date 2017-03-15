---
title: "CA1722：識別項不應使用不正確的前置字元 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1722：識別項不應使用不正確的前置字元
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 識別項具有不正確的前置字元。  
  
## 規則描述  
 根據慣例，只有特定程式設計項目的名稱會以特定的前置字元做為開頭。  
  
 型別名稱不具有特定的前置字元，因此不應該以 'C' 做為前置字元。  此規則會報告型別名稱的違規情況，例如 'CMyClass'，但不會報告像是 'Cache' 的型別名稱違規。  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短新軟體程式庫的學習過程，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 從識別項移除前置字元。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 相關規則  
 [CA1715：識別項名稱應該使用正確的前置字元](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)