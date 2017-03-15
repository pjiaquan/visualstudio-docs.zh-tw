---
title: "CA2215：Dispose 方法應該呼叫基底類別處置 | Microsoft Docs"
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
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215：Dispose 方法應該呼叫基底類別處置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 實作 <xref:System.IDisposable?displayProperty=fullName> 的型別會繼承自同樣實作 <xref:System.IDisposable> 的型別。  但是繼承型別的 <xref:System.IDisposable.Dispose%2A> 方法卻未呼叫父型別的 <xref:System.IDisposable.Dispose%2A> 方法。  
  
## 規則描述  
 如果型別會繼承自可處置的型別，則必須從本身的 <xref:System.IDisposable.Dispose%2A> 方法呼叫基底型別 \(Base Type\) 的 <xref:System.IDisposable.Dispose%2A> 方法。  呼叫基底型別方法 Dispose，確保會釋放由基底型別所建立的任何資源。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請呼叫 <xref:System.IDisposable.Dispose%2A> 方法中的 `base`.<xref:System.IDisposable.Dispose%2A>。  
  
## 隱藏警告的時機  
 如果 `base`.<xref:System.IDisposable.Dispose%2A> 的呼叫層級比規則的檢查層級更深層，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 在下列範例中，程式碼會顯示實作 <xref:System.IDisposable> 的型別 `TypeA`。  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## 範例  
 在下列範例中，程式碼會顯示繼承自型別 `TypeA` 並正確呼叫 <xref:System.IDisposable.Dispose%2A> 方法的型別 `TypeB`。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_1.vb)]  
  
## 請參閱  
 <xref:System.IDisposable?displayProperty=fullName>   
 [處置模式](../Topic/Dispose%20Pattern.md)