---
title: "CA2151：具有關鍵類型的欄位應為安全性關鍵 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2151：具有關鍵類型的欄位應為安全性關鍵
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 已宣告安全性透明欄位或安全性關鍵欄位。  它的指定類型為安全性關鍵類型。  例如：  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 在此範例中，`m_field` 是屬於安全性關鍵類型的安全性透明欄位。  
  
## 規則描述  
 若要使用安全性關鍵類型，參考該類型的程式碼必須是安全性關鍵或安全性安全關鍵。  即使是間接參考也是如此。  例如，當您參考屬於關鍵類型的透明欄位時，您的程式碼必須是安全性關鍵或安全性安全。  因此，使用安全性透明或安全性安全關鍵欄位容易發生錯誤，因為透明程式碼仍然無法存取該欄位。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請標示具有 <xref:System.Security.SecurityCriticalAttribute> 屬性的欄位，或是將該欄位所參考的類型設為安全性透明或安全性關鍵類型。  
  
```c#  
// Fix 1: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
// Fix 2: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   class Type1 { } // Type1 is now transparent  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
```  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
### 程式碼  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### 註解