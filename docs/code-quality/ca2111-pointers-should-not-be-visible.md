---
title: "CA2111：指標不應該為可見的 | Microsoft Docs"
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
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2111：指標不應該為可見的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的 <xref:System.IntPtr?displayProperty=fullName> 或 <xref:System.UIntPtr?displayProperty=fullName> 欄位都不是唯讀的。  
  
## 規則描述  
 <xref:System.IntPtr> 和 <xref:System.UIntPtr> 是用於存取 Unmanaged 記憶體的指標型別。  如果指標不是私用、內部或唯讀的，惡意的程式碼可變更指標值，進而可能會允許存取記憶體中的任意位置，或是造成應用程式或系統錯誤。  
  
 如果您想要保護對包含指標欄位之型別的存取，請參閱[CA2112：受保護類型不應公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。  
  
## 如何修正違規  
 使指標成為唯讀、內部或私用的，即可保護指標。  
  
## 隱藏警告的時機  
 如果您不依賴指標值，請隱藏此規則的警告。  
  
## 範例  
 下列程式碼會顯示違反和滿足規則的指標。  請注意，非私用指標也會違反規則[CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## 相關規則  
 [CA2112：受保護類型不應公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## 請參閱  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>