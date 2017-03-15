---
title: "CA2142：透明程式碼不可以使用 LinkDemand 加以保護 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2142：透明程式碼不可以使用 LinkDemand 加以保護
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 透明方法需要 <xref:System.Security.Permissions.SecurityAction> 或其他安全性要求。  
  
## 規則描述  
 需要 LinkDemand 才能存取的透明方法會引發這個規則。  安全性透明程式碼不應負責驗證作業的安全性，因此，不應要求權限。  由於透明方法的安全性應該是中立的，因此不應進行任何安全性決策。  此外，安全關鍵程式碼 \(不會進行安全性決策\) 不應該依賴透明程式碼在先前進行此類決策。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除透明方法的連結要求，若方法執行安全性檢查 \(例如安全性要求\)，則在方法標記 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 在下列範例中，由於方法是透明的而且標記了包含 <xref:System.Security.Permissions.SecurityAction> 的 LinkDemand <xref:System.Security.PermissionSet>，因此會引發規則。  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 請勿隱藏此規則的警告。