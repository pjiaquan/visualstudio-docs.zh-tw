---
title: "CA1506：應避免使用結合過度的類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1506：應避免使用結合過度的類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|分類|Microsoft.Maintainability|  
|中斷變更|中斷|  
  
## 原因  
 型別或方法與許多其他型別耦合。  
  
## 規則描述  
 這個規則會測量類別的耦合，方法是計算型別或方法包含的唯一型別參考數目。  
  
 具有高度類別耦合的型別或方法可能會難以維護。  比較好的辦法是讓型別和方法呈現出較低的耦合和較高的聚結性。  
  
## 如何修正違規  
 若要修正這個違規，請嘗試重新設計型別或方法，降低其耦合的型別數目。  
  
## 隱藏警告的時機  
 當型別或方法儘管與其他型別有大量的相依性卻仍判定為可維護時，請排除這個警告。  
  
## 請參閱  
 [維護性警告](../code-quality/maintainability-warnings.md)   
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)