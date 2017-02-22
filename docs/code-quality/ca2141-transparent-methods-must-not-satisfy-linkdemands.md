---
title: "CA2141：透明方法不可以滿足 LinkDemand | Microsoft Docs"
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
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2141：透明方法不可以滿足 LinkDemand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 安全性透明的方法會呼叫組件中的方法 \(此組件未標記 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) 屬性\)，或者安全性透明方法符合型別或方法的 <xref:System.Security.Permissions.SecurityAction>`.LinkDemand`。  
  
## 規則描述  
 滿足 LinkDemand 屬於安全性敏感作業，可能會在無意間造成權限提高。  安全性透明程式碼不能符合 LinkDemand，因為它不受限於與安全性關鍵程式碼相同的安全性稽核需求。  安全性規則集層級 1 組件中的透明方法將會使它們能夠滿足的所有 LinkDemands 在執行階段被轉換成完整要求，因此可能會導致效能問題。  在安全性規則集層級 2 組件中，如果透明方法嘗試滿足 LinkDemand，將無法編譯 Just\-In\-Time \(JIT\) 編譯器。  
  
 在使用層級 2 安全性的組件中，安全性透明方法滿足 LinkDemand 的嘗試，或在非 APTCA 組件中呼叫方法，就會引發 <xref:System.MethodAccessException>；在層級 1 組件中，LinkDemand 完全是視需要的。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請在存取方法標記 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性，或者從存取方法中移除 LinkDemand。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 在這個範例中，透明方法會嘗試呼叫具有 LinkDemand 的方法。  這個程式碼就會引發這個規則。  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]