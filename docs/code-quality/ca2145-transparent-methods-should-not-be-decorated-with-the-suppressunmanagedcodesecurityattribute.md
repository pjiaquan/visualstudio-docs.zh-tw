---
title: "CA2145：透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾 | Microsoft Docs"
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
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145：透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 透明方法、標記 <xref:System.Security.SecuritySafeCriticalAttribute> 的方法或包含標記 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性之方法的型別。  
  
## 規則描述  
 以 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性裝飾的方法會在任何方法呼叫它時放置隱含的 LinkDemand。  這個 LinkDemand 要求呼叫程式碼必須是安全性關鍵。  將使用 SuppressUnmanagedCodeSecurity 的方法標記 <xref:System.Security.SecurityCriticalAttribute> 屬性會使方法呼叫端的這個需求更為明顯。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請在方法或型別標記 <xref:System.Security.SecurityCriticalAttribute> 屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
### 程式碼  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### 註解