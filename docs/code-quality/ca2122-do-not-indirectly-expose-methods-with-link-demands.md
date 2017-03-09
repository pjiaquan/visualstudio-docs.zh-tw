---
title: "CA2122：不要間接公開具有連結要求的方法 | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122：不要間接公開具有連結要求的方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|分類|Microsoft.Security|  
|中斷變更|不中斷|  
  
## 原因  
 公用或保護的成員含有[Link Demands](../Topic/Link%20Demands.md)，而且是由未執行任何安全性檢查的成員所呼叫。  
  
## 規則描述  
 連結要求只會檢查立即呼叫端的使用權限。  如果成員 `X` 沒有對呼叫端提出任何安全性要求，並呼叫連結要求所保護的程式碼，則不具所需權限的呼叫端即可使用 `X` 存取 protected 成員。  
  
## 如何修正違規  
 將安全性[資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)或連結要求加入至成員，以便讓它不再提供對連結要求的 protected 成員進行不安全存取。  
  
## 隱藏警告的時機  
 若要放心地隱藏這項規則的警告，您必須確定程式碼不會授與呼叫端存取作業或資源的權限，因為這種存取權限可能會遭到惡意使用。  
  
## 範例  
 下列範例會顯示違反規則的程式庫，以及示範程式庫弱點的應用程式。  範例程式庫所提供的這兩種方法都會違反規則。  `EnvironmentSetting` 方法會受到連結要求的保護，以防不限制地存取環境變數。  在呼叫 `EnvironmentSetting` 之前，`DomainInformation` 方法不會對其呼叫端提出任何安全性要求。  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## 範例  
 下列應用程式會呼叫不安全的程式庫成員。  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 這個範例產生下列輸出。  
  
  **無安全性的成員值：seattle.corp.contoso.com**   
## 請參閱  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)