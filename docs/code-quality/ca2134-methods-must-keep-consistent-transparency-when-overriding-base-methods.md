---
title: "CA2134：覆寫基底方法時，方法必須保持一致的透明度 | Microsoft Docs"
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
  - "CA2134"
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2134：覆寫基底方法時，方法必須保持一致的透明度
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 當標記 <xref:System.Security.SecurityCriticalAttribute> 的方法覆寫透明或標記 <xref:System.Security.SecuritySafeCriticalAttribute> 的方法時，就會引發這個規則。  透明或標記 <xref:System.Security.SecuritySafeCriticalAttribute> 的方法覆寫標記 <xref:System.Security.SecurityCriticalAttribute> 的方法時，也會引發規則。  
  
 覆寫虛擬方法或實作介面時會套用此規則。  
  
## 規則描述  
 嘗試變更繼承鏈結上一層方法的安全性存取範圍時，就會引發這個規則。  例如，如果基底類別中的虛擬方法是透明的或安全關鍵，衍生類別就必須以透明的或安全關鍵方法覆寫它。  相反地，如果虛擬具有安全性關鍵，衍生類別必須以安全性關鍵方法覆寫它。  實作介面方法適用相同的規則。  
  
 當程式碼是 JIT 編譯而不是在執行階段時編譯 \(因此透明度計算不具有動態型別資訊\)，就會強制透明度規則。  因此，透明度計算結果必須能只從 JIT 編譯的靜態型別決定，而不論其動態型別。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請變更方法的透明度，此方法會覆寫虛擬方法或實作介面，以比對虛擬或介面方法的透明度。  
  
## 隱藏警告的時機  
 不隱藏此規則的警告。  違反這個規則會導致使用層級 2 透明度的組件發生執行階段 <xref:System.TypeLoadException>。  
  
## 範例  
  
### 程式碼  
 [!CODE [FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency#1)]  
  
## 請參閱  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)