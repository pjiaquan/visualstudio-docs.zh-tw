---
title: "CA2133：委派必須繫結至透明度一致的方法 | Microsoft Docs"
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
  - "CA2133"
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2133：委派必須繫結至透明度一致的方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
> [!NOTE]
>  這個警告只會套用至執行 CoreCLR \(專屬於 Silverlight Web 應用程式的 CLR 版本\) 的程式碼。  
  
## 原因  
 若方法將標記 <xref:System.Security.SecurityCriticalAttribute> 的委派繫結至透明或標記 <xref:System.Security.SecuritySafeCriticalAttribute> 的方法，就會引發這個警告。  此警告也會引發將透明或安全關鍵性的委派繫結至關鍵方法的方法。  
  
## 規則描述  
 委派型別及所繫結的方法必須具有一致的透明度。  透明和安全關鍵的委派只能繫結至其他透明或安全關鍵的方法。  同樣地，關鍵委派只能繫結至關鍵方法。  這些繫結規則可確保唯一可以透過委派叫用方法的程式碼也可以直接叫用同樣的方法。  例如，繫結規則可防止透明的程式碼直接透過透明委派呼叫關鍵程式碼。  
  
## 如何修正違規  
 若要修正這項警告的違規情形，請變更委派的透明度，或者變更它所繫結之方法的透明度，使兩者的透明度相等。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
### 程式碼  
 [!code-cs[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]