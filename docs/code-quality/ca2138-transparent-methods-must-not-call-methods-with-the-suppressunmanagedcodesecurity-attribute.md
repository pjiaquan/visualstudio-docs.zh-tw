---
title: "CA2138：透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法 | Microsoft Docs"
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
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138：透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 安全性透明方法會呼叫標示 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性的方法。  
  
## 規則描述  
 任何直接呼叫原生程式碼的透明方法都會引發此規則，例如使用透過 P\/Invoke \(平台叫用\) 呼叫。  標記 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性的 P\/Invoke 和 COM Interop 方法會針對呼叫方法完成 LinkDemand。  由於安全性透明的程式碼無法滿足 LinkDemands，所以程式碼也無法呼叫標示 SuppressUnmanagedCodeSecurity 屬性的方法，或是標示 SuppressUnmanagedCodeSecurity 屬性的類別方法。  此方法將失敗，或要求將轉換為完全要求。  
  
 違反這個規則會在層級 2安全性透明模型中導致 <xref:System.MethodAccessException>，並且在層級 1 透明模型中導致對 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> 的完整需求。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性，並在方法標記 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]