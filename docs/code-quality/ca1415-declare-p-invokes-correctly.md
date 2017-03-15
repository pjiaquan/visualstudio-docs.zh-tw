---
title: "CA1415：P/Invokes 必須正確宣告 | Microsoft Docs"
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
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415：P/Invokes 必須正確宣告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|分類|Microsoft.Interoperability|  
|中斷變更|非中斷 \- 如果無法在組件外部看見宣告參數的 P\/Invoke。  中斷 \- 如果可以在組件外部看見宣告參數的 P\/Invoke。|  
  
## 原因  
 不正確地宣告平台叫用 \(Invoke\) 方法。  
  
## 規則描述  
 平台叫用方法會存取 Unmanaged 程式碼，而且是使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中之 `Declare` 關鍵字或 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 所定義的。  目前，此規則會尋找以 Win32 函式為目標 \(具有指向 OVERLAPPED 結構參數的指標\) 的平台叫用方法宣告，且相對應的 Managed 參數不是指向 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 結構的指標。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請正確地宣告平台叫用方法。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反此規則和滿足此規則的平台叫用方法。  
  
 [!CODE [FxCop.Interoperability.DeclarePInvokes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes#1)]  
  
## 請參閱  
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)