---
title: "CA1708：識別項名稱不應該只靠大小寫區別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1708：識別項名稱不應該只靠大小寫區別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 有兩個型別、成員、參數或完整命名空間的名稱在轉換為小寫時完全相同。  
  
## 規則描述  
 因為以 Common Language Runtime 為目標的語言不需要區分大小寫，因此，命名空間、型別、成員和參數的識別項不能只有大小寫的不同。  例如，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 是最常用之不區分大小寫的語言。  
  
 這個規則僅會針對公開可見的成員引發。  
  
## 如何修正違規  
 選取以不區分大小寫的方式與其他識別項比較時，仍具有唯一性的名稱。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  可能會無法在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的所有可用語言中使用程式庫。  
  
## 違規範例  
 下列範例示範這項規則的違規情形。  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## 相關規則  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)