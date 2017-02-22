---
title: "CA2147：透明的方法不可以使用安全性判斷提示 | Microsoft Docs"
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
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2147：透明的方法不可以使用安全性判斷提示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 標記為 <xref:System.Security.SecurityTransparentAttribute> 的程式碼並未具備足夠的使用權限可以進行判斷提示 \(Assert\)。  
  
## 規則描述  
 此規則會分析完全透明或混合透明\/關鍵之組件 \(Assembly\) 中的所有方法和型別，並將 <xref:System.Security.CodeAccessPermission.Assert%2A> 的任何宣告式或必要用法加上旗標。  
  
 在執行階段，從透明程式碼對 <xref:System.Security.CodeAccessPermission.Assert%2A> 所做的任何呼叫都會導致擲回 <xref:System.InvalidOperationException> 的情況。  100% 透明的組件，以及混合的透明\/關鍵組件 \(其中的方法或型別宣告為透明，但包含宣告式或必要的判斷提示\)，都有可能發生這種問題。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 引入一項名為「*透明度*」\(Transparency\) 的功能。  個別方法、欄位、介面、類別和型別可以是透明或關鍵項目。  
  
 不能使用透明程式碼來評估安全性權限。  因此，其已授與或要求的任何使用權限都會自動透過程式碼傳遞至呼叫端或主機應用程式定義域。  權限升級的範例包括 Assert、LinkDemand、SuppressUnmanagedCode 以及 `unsafe` 程式碼。  
  
## 如何修正違規  
 若要解決這個問題，請將呼叫判斷提示的程式碼標記為 <xref:System.Security.SecurityCriticalAttribute>，或是移除判斷提示。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的訊息。  
  
## 範例  
 在 `Assert` 方法擲回 <xref:System.InvalidOperationException> 時，如果 `SecurityTestClass` 是透明的，這個程式碼就會失敗。  
  
 [!CODE [FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts#1)]  
  
## 範例  
 其中一個選項是程式碼檢閱下列範例中的 SecurityTransparentMethod 方法，如果認為該方法可安全提升，就將SecurityTransparentMethod 標記為安全關鍵。這樣做必須針對該方法執行詳細、完整且零錯誤的安全性稽查，同時檢查 Assert 之下發生在方法內的任何 call\-out：  
  
 [!CODE [FxCop.Security.SecurityTransparentCode2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2#1)]  
  
 另一個選擇是從程式碼中移除判斷提示，並讓任何後續的檔案 I\/O 使用權限要求越過 SecurityTransparentMethod 流入呼叫端，以便進行安全性檢查。  這可啟用安全性檢查。  此時通常不需要安全性稽核，因為使用權限要求會流入呼叫端和\/或應用程式定義域中。  使用權限要求需透過安全性原則、裝載環境和程式碼來源使用權限的授與加以嚴密控制。  
  
## 請參閱  
 [安全性警告](../code-quality/security-warnings.md)