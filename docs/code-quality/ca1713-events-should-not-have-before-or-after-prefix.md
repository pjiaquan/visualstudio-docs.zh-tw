---
title: "CA1713：事件不應有 before 或 after 前置字元 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
  - "CA1713"
helpviewer_keywords: 
  - "CA1713"
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1713：事件不應有 before 或 after 前置字元
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 事件的名稱會以 'Before' 或 'After' 為開頭。  
  
## 規則描述  
 事件名稱應該會描述引發事件的動作。  若要命名在特定序列 \(Sequence\) 中引發的相關事件，請使用現在式或過去式表示動作序列相對的位置。  例如，在為關閉資源時所引發的一對事件命名時，可能會將事件命名為 'Closing' 和 'Closed'，而不是 'BeforeClose' 和 'AfterClose'。  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短新軟體程式庫的學習過程，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 從事件名稱中移除前置字元，並考慮變更名稱以使用動詞的現在式或過去式。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。