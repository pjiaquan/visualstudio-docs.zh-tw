---
title: "CA1724：類型名稱不應該和命名空間相符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1724：類型名稱不應該和命名空間相符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 在不區分大小寫的比較中符合 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 命名空間的型別名稱。  
  
## 規則描述  
 型別名稱不得符合 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Class Library 中定義的命名空間名稱。  違反此規則會降低程式庫的可用性。  
  
## 如何修正違規  
 選取不符合 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 類別庫命名空間之名稱的型別名稱。  
  
## 隱藏警告的時機  
 在新的程式開發中，尚未有必須隱藏此規則之警告的案例出現。  隱藏警告之前，請仔細考慮程式庫使用者可能會被相符名稱混淆的情況。  對於隨附的程式庫，您可能必須隱藏這項規則的警告。