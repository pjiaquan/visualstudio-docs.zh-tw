---
title: "CA1049：擁有原生資源的類型應為可處置 | Microsoft Docs"
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
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049：擁有原生資源的類型應為可處置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 型別會參考 <xref:System.IntPtr?displayProperty=fullName> 欄位、<xref:System.UIntPtr?displayProperty=fullName> 欄位或 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> 欄位，但不會實作 <xref:System.IDisposable?displayProperty=fullName>。  
  
## 規則描述  
 此規則假設 <xref:System.IntPtr>、<xref:System.UIntPtr> 和 <xref:System.Runtime.InteropServices.HandleRef> 欄位會儲存 Unmanaged 資源的指標。  配置 Unmanaged 資源的型別應實作 <xref:System.IDisposable>，讓呼叫端視需求釋放這些資源，並且縮短儲存資源之物件的存留期 \(Lifetime\)。  
  
 建議用以清除 Unmanaged 資源的設計模式就是同時提供隱含和明確方式，以便分別使用 <xref:System.Object.Finalize%2A?displayProperty=fullName> 方法和 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法釋放這些資源。  記憶體回收行程會在物件判斷為不可再執行後的某個不定時間，呼叫物件的 <xref:System.Object.Finalize%2A> 方法。  在呼叫 <xref:System.Object.Finalize%2A> 之後，須有其他記憶體回收行程才能釋放物件。  <xref:System.IDisposable.Dispose%2A> 方法允許呼叫端依照需求明確釋放資源，並且比資源交給記憶體回收行程還早釋放。  在清除 Unmanaged 資源之後，<xref:System.IDisposable.Dispose%2A> 應該呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 方法，讓記憶體回收行程知道不再需要呼叫 <xref:System.Object.Finalize%2A>。這可以消除其他記憶體回收行程的需求，並且縮短物件的存留期。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請實作 <xref:System.IDisposable>。  
  
## 隱藏警告的時機  
 如果型別未參考 Unmanaged 資源，則您可以放心地隱藏這項規則的警告。  否則，請勿隱藏這項規則的警告，因為實作 <xref:System.IDisposable> 失敗會導致 Unmanaged 資源無法使用或無法加以充分利用。  
  
## 範例  
 下列範例顯示的型別會實作 <xref:System.IDisposable> 以清除 Unmanaged 資源。  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## 相關規則  
 [CA2115：使用原生資源時必須呼叫 GC.KeepAlive](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816：正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216：可處置類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001：具有可處置欄位的類型應該是可處置的](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)  
  
## 請參閱  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [處置模式](../Topic/Dispose%20Pattern.md)