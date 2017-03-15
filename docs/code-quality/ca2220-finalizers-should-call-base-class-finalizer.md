---
title: "CA2220：完成項應該呼叫基底類別完成項 | Microsoft Docs"
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
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220：完成項應該呼叫基底類別完成項
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 覆寫 <xref:System.Object.Finalize%2A?displayProperty=fullName> 的型別不會在它的基底類別中呼叫 <xref:System.Object.Finalize%2A> 方法。  
  
## 規則描述  
 最終化必須透過繼承階層架構 \(Inheritance Hierarchy\) 進行傳播。  若要確定這一點，則型別必須從它們自己的 <xref:System.Object.Finalize%2A> 方法呼叫基底類別 <xref:System.Object.Finalize%2A>。  C\# 編譯器會自動將呼叫加入到基底類別完成項。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請從您的 <xref:System.Object.Finalize%2A> 方法呼叫基底型別的 <xref:System.Object.Finalize%2A> 方法。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  有些目標為 Common Language Runtime 的編譯器會將基底型別的完成項插入 Microsoft Intermediate Language \(MSIL\)。  如果報告這項規則的警告，則編譯器不會插入該呼叫，而您必須將它加入至程式碼。  
  
## 範例  
 下列 Visual Basic 範例會顯示在它的基底類別中正確呼叫 <xref:System.Object.Finalize%2A> 方法的型別 `TypeB`。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## 請參閱  
 [處置模式](../Topic/Dispose%20Pattern.md)