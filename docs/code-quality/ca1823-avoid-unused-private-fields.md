---
title: "CA1823：避免包含未使用的私用欄位 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1823：避免包含未使用的私用欄位
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 當程式碼中有私用 \(Private\) 欄位，但沒有任何程式碼路徑會用到該欄位時，則會回報此規則。  
  
## 規則描述  
 偵測到似乎不能在組件內存取的私用欄位。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除欄位或加入使用此欄位的程式碼。  
  
## 隱藏警告的時機  
 您可以放心地隱藏這項規則的警告。  
  
## 相關規則  
 [CA1812：避免使用未執行個體化的內部類別](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801：必須檢視未使用的參數](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811：避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)