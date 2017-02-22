---
title: "CA2140：透明程式碼不可以參考安全性關鍵項目 | Microsoft Docs"
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
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2140：透明程式碼不可以參考安全性關鍵項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 透明方法：  
  
-   處理安全性關鍵的安全性例外狀況型別  
  
-   具有標示為安全性關鍵型別的參數  
  
-   具有含安全性關鍵條件約束的泛型參數  
  
-   具有安全性關鍵型別的區域變數  
  
-   參考標示為安全性關鍵的型別  
  
-   呼叫標記為安全性關鍵的方法  
  
-   參考標示為安全性關鍵的欄位  
  
-   傳回標示為安全性關鍵的型別  
  
## 規則描述  
 標示 <xref:System.Security.SecurityCriticalAttribute> 屬性的程式碼項目具安全性關鍵。   透明方法不能使用安全性關鍵項目。  如果透明型別嘗試使用安全性關鍵型別，就會引發 <xref:System.TypeAccessException>、<xref:System.MethodAccessException> 或 <xref:System.FieldAccessException>。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請執行下列其中一項：  
  
-   將使用安全性關鍵程式碼的程式碼項目標記 <xref:System.Security.SecurityCriticalAttribute> 屬性  
  
     \-或\-  
  
-   從標記為安全性關鍵的程式碼項目中移除 <xref:System.Security.SecurityCriticalAttribute> 屬性，改將其標記為 <xref:System.Security.SecuritySafeCriticalAttribute> 或 <xref:System.Security.SecurityTransparentAttribute> 屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 在下列範例中，透明方法會嘗試參考安全性關鍵泛型集合、安全性關鍵欄位，以及安全性關鍵方法。  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## 請參閱  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>