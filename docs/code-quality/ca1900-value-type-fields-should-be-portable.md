---
title: "CA1900：實值類型欄位應該為可移植的 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1900"
  - "ValueTypeFieldsShouldBePortable"
helpviewer_keywords: 
  - "ValueTypeFieldsShouldBePortable"
  - "CA1900"
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1900：實值類型欄位應該為可移植的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|分類|Microsoft.Portability|  
|中斷變更|中斷 \- 如果可以在組件外部看見該欄位。<br /><br /> 非中斷 \- 如果無法在組件外部看見型別。|  
  
## 原因  
 這個規則會檢查在 64 位元作業系統上封送處理 Unmanaged 程式碼時，宣告為明確配置的結構是否會正確地配置。  IA\-64 不允許存取未配置的記憶體，而且如果無法修正此項違規，則此處理序 \(Process\) 會造成當機。  
  
## 規則描述  
 具有明確配置的結構，其配置中包含會造成 64 位元作業系統當機的不當欄位。  
  
## 如何修正違規  
 小於 8 個位元組的所有欄位，都必須要有自身大小的倍數的位移，具有 8 個位元組或以上大小的欄位，則必須要有 8 的倍數的位移。  另一個解決方法是在合理情況下，使用 `LayoutKind.Sequential` 而非 `LayoutKind.Explicit`。  
  
## 隱藏警告的時機  
 這則警告只有在發生錯誤時才能隱藏。