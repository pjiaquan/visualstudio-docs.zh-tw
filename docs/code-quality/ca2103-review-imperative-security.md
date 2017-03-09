---
title: "CA2103：必須檢視命令式安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
helpviewer_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2103：必須檢視命令式安全性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 方法會使用命令式安全性，而且可能會利用只要要求正在使用中就可能變更的狀態資訊或傳回值建構權限。  
  
## 規則描述  
 在程式碼執行期間，命令式安全性會使用 Managed 物件指定使用權限和安全性動作，相較於宣告式安全性，後者會使用屬性 \(Attribute\) 儲存中繼資料 \(Metadata\) 中的使用權限和動作。  命令式安全性非常有彈性，讓您能使用無法在執行階段之前取得的資訊，設定權限物件的狀態並選取安全性動作。  這種彈性會有風險隨之而來，也就是說只要動作生效，您用於決定使用權限狀態的執行階段資訊就無法維持不變。  
  
 請盡可能使用宣告式安全性。  宣告式要求比較容易了解。  
  
## 如何修正違規  
 檢查命令式安全性要求，確保使用權限的狀態不會依賴因使用權限正在使用中而變更的資訊。  
  
## 隱藏警告的時機  
 如果使用權限不依賴變更資料，則您可以放心地隱藏這項規則的警告。  但是，最好是將命令式要求變更為其宣告式的對等用法。  
  
## 請參閱  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)