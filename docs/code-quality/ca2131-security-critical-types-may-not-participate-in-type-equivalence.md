---
title: "CA2131：安全性關鍵類型可能未參與類型等價 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131：安全性關鍵類型可能未參與類型等價
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 加入型別相等及型別本身或型別的成員或欄位的型別會標記 <xref:System.Security.SecurityCriticalAttribute> 屬性。  
  
## 規則描述  
 此規則會引發任何關鍵的型別或包含參與型別等價之關鍵方法或欄位的型別。  當 CLR 偵測到此類型別時，會無法在執行階段以 <xref:System.TypeLoadException> 載入。  通常，只有在使用者手動實作型別等價，而不是依賴 tlbimp 和編譯器進行型別等價時，就會引發這項規則。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除 SecurityCritical 屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例示範會引發這個規則的介面、方法和欄位。  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## 請參閱  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)