---
title: "CA1048：不要在密封類型中宣告 virtual 成員 | Microsoft Docs"
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
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1048：不要在密封類型中宣告 virtual 成員
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 public 型別為密封的，並宣告為 `virtual` \(在 Visual Basic 中則為 `Overridable`\) 且不是最終的方法。  這項規則不會報告委派型別 \(Delegate Type\) 的違規，這些型別必須遵循這個模式。  
  
## 規則描述  
 型別會將方法宣告為 virtual，讓繼承型別可以覆寫 virtual 方法的實作。  根據定義，您無法繼承自密封型別，因此使得密封型別上的 virtual 方法失去意義。  
  
 Visual Basic .NET 和 C\# 編譯器 \(Compiler\) 不允許型別違反這項規則。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請讓方法成為非虛擬或讓型別成為可繼承的。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  使型別保持它的目前狀態可能會造成維護問題，而且不會提供任何好處。  
  
## 範例  
 下列範例顯示違反此規則的型別。  
  
 [!CODE [FxCop.Design.SealedVirtual#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual#1)]