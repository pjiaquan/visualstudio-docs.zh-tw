---
title: "CA2149：透明方法不可以呼叫機器碼 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2149"
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2149：透明方法不可以呼叫機器碼
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 方法會呼叫 P\/Invoke 之類的方法 Stub 呼叫原生函式。  
  
## 規則描述  
 任何直接呼叫機器碼的透明方法都會引發此規則，例如透過 P\/Invoke。  違反這個規則會在層級 2安全性透明模型中導致 <xref:System.MethodAccessException>，並且在層級 1 透明模型中導致對 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> 的完整需求。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請在呼叫機器碼的方法標記 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 [!CODE [FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode#1)]