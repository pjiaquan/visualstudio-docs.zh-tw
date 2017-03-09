---
title: "CA2213：可處置的欄位應該受到處置 | Microsoft Docs"
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
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213：可處置的欄位應該受到處置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 實作 <xref:System.IDisposable?displayProperty=fullName> 的型別宣告了也實作 <xref:System.IDisposable> 之型別的欄位。  宣告型別的 <xref:System.IDisposable.Dispose%2A> 方法不會呼叫欄位的 <xref:System.IDisposable.Dispose%2A> 方法。  
  
## 規則描述  
 型別會負責處置它的所有 Unmanaged 資源，透過實作 <xref:System.IDisposable> 便可達成此目的。  此規則會檢查可處置型別 `T` 所宣告的欄位 `F` 是否為可處置型別 `FT` 的執行個體。  對每個欄位 `F` 而言，此規則會嘗試找出對 `FT.Dispose` 的呼叫。  此規則會搜尋 `T.Dispose` 所呼叫的方法和更下一層的方法 \(由 `FT.Dispose` 呼叫的方法所呼叫的方法\)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，而且您也負責配置和釋放欄位所保留的 Unmanaged 資源，請在屬於實作 <xref:System.IDisposable> 之型別的欄位上呼叫 <xref:System.IDisposable.Dispose%2A>。  
  
## 隱藏警告的時機  
 如果您不負責釋放欄位所保留的資源，或者會在比規則檢查更深的呼叫層級中呼叫 <xref:System.IDisposable.Dispose%2A>，則可以放心地隱藏這項規則的警告。  
  
## 範例  
 在下列範例中，程式碼會顯示實作 <xref:System.IDisposable> 的 `TypeA` 型別 \(前述的 `FT`\)。  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## 範例  
 下列範例顯示 `TypeB` 型別，此型別違反此規則而將欄位 \(`aFieldOfADisposableType`，即在前面討論中的 `F`\) 宣告為為可處置型別 \(`TypeA`\)，而不呼叫欄位上 <xref:System.IDisposable.Dispose%2A>。  `TypeB` 對應於先前討論過的  `T`。  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## 請參閱  
 <xref:System.IDisposable?displayProperty=fullName>   
 [處置模式](../Topic/Dispose%20Pattern.md)