---
title: "CA1044：屬性不應為唯寫 | Microsoft Docs"
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
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1044：屬性不應為唯寫
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的屬性具有 set 存取子 \(Accessor\)，但沒有 get 存取子。  
  
## 規則描述  
 Get 存取子會提供屬性的讀取權限，而 set 存取子則提供寫入權限。  雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。  這是因為讓使用者設定一個值，然後防止使用者檢視該值並不會提供任何安全性。  同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將 get 存取子加入至屬性。  此外，如果需要唯寫屬性行為，請考慮將這個屬性轉換為方法。  
  
## 隱藏警告的時機  
 強烈建議您不要隱藏此規則的警告。  
  
## 範例  
 在下列範例中，`BadClassWithWriteOnlyProperty` 是具有唯寫屬性的型別。  `GoodClassWithReadWriteProperty` 包含修正過的程式碼。  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]