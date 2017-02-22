---
title: "CA1719：參數名稱不應符合成員名稱 | Microsoft Docs"
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
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1719：參數名稱不應符合成員名稱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 在不區分大小寫的比較中，外部可見成員的名稱會符合其中一個參數的名稱。  
  
## 規則描述  
 參數名稱應該要能傳達參數的意義，而成員名稱應該要能傳達成員的意義。  兩者相同屬罕見的設計。  如果將參數命名為與成員名稱相同的名稱，則不僅會不容易了解，也會讓程式庫難以使用。  
  
## 如何修正違規  
 選取不符合成員名稱的參數名稱。  
  
## 隱藏警告的時機  
 在新的程式開發中，尚未有必須隱藏此規則之警告的案例出現。  對於隨附的程式庫，您可能必須隱藏這項規則的警告。  
  
## 相關規則  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：識別項不應包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)