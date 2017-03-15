---
title: "CA1403：自動配置類型不應該是 COM 可見 | Microsoft Docs"
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
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403：自動配置類型不應該是 COM 可見
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 元件物件模型 \(COM\) 可見的實值型別是以設定為 <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> 的 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 屬性所標記。  
  
## 規則描述  
 <xref:System.Runtime.InteropServices.LayoutKind> 配置型別是由 Common Language Runtime 所管理。  可以在 .NET Framework 的版本間變更這些型別的配置，這將會中斷必須有特定配置的 COM 用戶端。  請注意如果未指定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性，則 C\#、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 C\+\+ 編譯器會指定實值型別的 <xref:System.Runtime.InteropServices.LayoutKind> 配置。  
  
 除非已標記，否則所有公用的非泛型型別對 COM 皆為可見的，而所有非公用的泛型型別對 COM 則皆不可見的。  但是，為了減少誤報的情形，這項規則要求必須明確陳述此型別的 COM 可視性、必須使用設定為 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 來標記包含的組件，而且必須使用設定為 `true` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 來標記此型別。  
  
## 如何修正違規  
 若要修正這項規則的違規情形，請將 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性的值變更為 <xref:System.Runtime.InteropServices.LayoutKind> 或 <xref:System.Runtime.InteropServices.LayoutKind>，或標記 COM 看不見的型別。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的型別和滿足規則的型別。  
  
 [!CODE [FxCop.Interoperability.AutoLayout#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout#1)]  
  
## 相關規則  
 [CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## 請參閱  
 [Introducing the Class Interface](http://msdn.microsoft.com/zh-tw/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [限定互通的 .NET 類型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)