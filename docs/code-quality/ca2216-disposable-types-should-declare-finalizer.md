---
title: "CA2216：可處置類型應該宣告完成項 | Microsoft Docs"
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
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216：可處置類型應該宣告完成項
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 實作 <xref:System.IDisposable?displayProperty=fullName> 且具有建議 Unmanaged 資源用法之欄位的型別，未實作如 <xref:System.Object.Finalize%2A?displayProperty=fullName> 所述的完成項。  
  
## 規則描述  
 如果可處置型別包含下列型別的欄位，就會報告違反此規則：  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## 如何修正違規  
 若要修正此規則的違規情形，請實作會呼叫 <xref:System.IDisposable.Dispose%2A> 方法的完成項。  
  
## 隱藏警告的時機  
 如果該型別並未實作 <xref:System.IDisposable> 以達到釋放 Unmanaged 資源的目的，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例顯示違反此規則的型別。  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## 相關規則  
 [CA2115：使用原生資源時必須呼叫 GC.KeepAlive](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816：正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049：擁有原生資源的類型應為可處置](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## 請參閱  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [處置模式](../Topic/Dispose%20Pattern.md)