---
title: "CA1052：靜態預留位置類型應該為密封的 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1052：靜態預留位置類型應該為密封的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別只包含靜態 \(Static\) 成員，因此不會利用 [密封](/dotnet/csharp/language-reference/keywords/sealed) \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\) 修飾詞 \(Modifier\) 宣告它們。  
  
## 規則描述  
 這項規則會假設只包含靜態成員的型別不是設計為繼承的，因為該型別不會提供可以在衍生型別 \(Derived Type\) 中加以覆寫的任何功能。  預定不會繼承的型別應該以 `sealed` 修飾詞標記，以允許使用它做為基底型別 \(Base Type\)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將型別標示為 `sealed`。  如果是以 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 \(含\) 以前的版本為目標，比較好的做法是將型別標記為 `static`。  使用這個方式，您可以避免必須宣告私用建構函式，以防止建立類別。  
  
## 隱藏警告的時機  
 只有在型別是設計為繼承的，才能隱藏這項規則的警告。  缺少 `sealed` 修飾詞，表示型別與基底型別一樣有用。  
  
## 違規範例  
  
### 描述  
 下列範例顯示違反規則的型別。  
  
### 程式碼  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## 使用 Static 修飾詞進行修正  
  
### 描述  
 下列範例顯示如何藉由使用 `static` 修飾詞標記型別來修正這個規則的違規。  
  
### 程式碼  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## 相關規則  
 [CA1053：靜態預留位置類型不應包含建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)