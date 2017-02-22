---
title: "CA1050：在命名空間中宣告類型 | Microsoft Docs"
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
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1050：在命名空間中宣告類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別被定義在具名命名空間的範圍之外。  
  
## 規則描述  
 型別會在命名空間中宣告以防止名稱衝突，而且可當做組織物件階層架構中相關型別的一種方法。  在任何具名命名空間之外的型別會在全域命名空間中 \(該全域命名空間不可在程式碼中參考\)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將型別放置在命名空間中。  
  
## 隱藏警告的時機  
 雖然不一定要隱藏這項規則的警告，但是當此組件 \(Assembly\) 絕對不會和其他組件一起使用時，這麼做並沒有安全顧慮。  
  
## 範例  
 下列範例顯示具有在命名空間外未正確宣告之型別的程式庫，以及在命名空間中以相同名稱宣告的型別。  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## 範例  
 下列應用程式會使用先前定義的程式庫。  請注意，當名稱 `Test` 不符合命名空間的資格時，會建立在命名空間之外宣告的型別。  另外必須注意的是，若要存取 `Goodspace` 中的 `Test` 型別，則必須有命名空間名稱。  
  
 [!CODE [FxCop.Design.TestTypesLive#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive#1)]