---
title: "CA2123：覆寫連結要求應該與基底相同 | Microsoft Docs"
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
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123：覆寫連結要求應該與基底相同
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 公用型別中之公用或保護的方法會覆寫方法或實作介面，而且沒有與介面或虛擬方法相同的[Link Demands](../Topic/Link%20Demands.md)。  
  
## 規則描述  
 這項規則會使方法符合它的基底方法，即另一個型別中的介面或虛擬方法，然後比較每個方法上的連結要求。  如果方法或基底方法具有連結要求，但另一個方法卻沒有，將會報告違規。  
  
 如果違反這項規則，則惡意呼叫端只需呼叫不安全的方法，就可以略過連結要求。  
  
## 如何修正違規  
 若要修正此規則的違規，請將同一個連結要求套用至覆寫方法或實作。  如果這樣不可能，請以完整要求標記方法，或是完全移除屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示這項規則的各種違規。  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## 請參閱  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)