---
title: "CA1816：正確呼叫 GC.SuppressFinalize | Microsoft Docs"
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
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816：正確呼叫 GC.SuppressFinalize
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|分類|Microsoft。  使用方式|  
|中斷變更|不中斷|  
  
## 原因  
  
-   屬於 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 實作的方法不會呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
-   不屬於 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 實作的方法會呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
-   呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>，並傳遞不同於 this \(在 Visual Basic 中為 Me\) 之值的方法。  
  
## 規則描述  
 在物件可讓記憶體回收之前，<xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法讓使用者可以隨時釋放資源。  如果呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法，則會釋放物件的資源。  這使得不需要最終處理。  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 應該呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>，以便讓記憶體回收行程不會呼叫物件的完成項。  
  
 若要避免使用完成項的衍生類別需要重新實作 [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) 以及呼叫它，未使用完成項的非密封型別仍應該呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
## 如何修正違規  
 若要修正此規則的違規情形：  
  
 如果方法是 <xref:System.IDisposable.Dispose%2A> 的實作，請將呼叫加入至 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>。  
  
 如果方法不是 <xref:System.IDisposable.Dispose%2A> 的實作，請移除對 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的呼叫，或將其移至型別的 <xref:System.IDisposable.Dispose%2A> 實作。  
  
 變更 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的所有呼叫以傳遞 this \(Visual Basic 中的 Me\)。  
  
## 隱藏警告的時機  
 只有在考慮使用 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 控制其他物件的存留期時，才隱藏這項規則的警告。  如果 <xref:System.IDisposable.Dispose%2A> 的實作並未呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>，請勿隱藏這項規則的警告。  在這種情況下，無法隱藏最終化將會降低效能且不提供任何好處。  
  
## 範例  
 下列範例會示範不正確呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的方法。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## 範例  
 下列範例示範以正確方式呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 的方法。  
  
 [!CODE [FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1)]  
  
## 相關規則  
 [CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216：可處置類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## 請參閱  
 [處置模式](../Topic/Dispose%20Pattern.md)