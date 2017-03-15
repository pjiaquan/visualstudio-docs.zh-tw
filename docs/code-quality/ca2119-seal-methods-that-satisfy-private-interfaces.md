---
title: "CA2119：密封方法以滿足私用介面的要求 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2119：密封方法以滿足私用介面的要求
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 可繼承的公用 \(Public\) 型別會提供 `internal` \(在 Visual Basic 中為 `Friend`\) 介面的可覆寫方法實作。  
  
## 規則描述  
 介面方法具有公用存取範圍，不能由實作類型變更。  內部介面會建立不要在定義介面之組件 \(Assembly\) 外部實作的合約。  使用 `virtual` \(在 Visual Basic 中為 `Overridable`\) 修飾詞 \(Modifier\) 實作內部介面方法的公用型別，允許組件外部的衍生型別 \(Derived Type\) 覆寫此方法。  如果定義組件中有第二個型別會呼叫此方法，且預期會有一份只於內部實作的合約，則在執行外部組件中的覆寫方法之後，可能會影響此行為。  這會產生安全性弱點。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請利用下列其中一種方式，防止方法在組件外部遭到覆寫：  
  
-   讓宣告型別為 `sealed` \(在 Visual Basic 中為 `NotInheritable`\)。  
  
-   將宣告型別的存取範圍變更為 `internal` \(在 Visual Basic 中為 `Friend`\)。  
  
-   移除宣告型別中的所有公用建構函式。  
  
-   不要使用 `virtual` 修飾詞實作方法。  
  
-   明確地實作方法。  
  
## 隱藏警告的時機  
 在詳細檢閱之後，若方法會在組件外部遭到覆寫但卻不會有可能被利用的安全性問題存在，則您可以放心地隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反此規則的型別 `BaseImplementation`。  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## 範例  
 下列範例會利用虛擬方法實作上一個範例。  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## 請參閱  
 [介面](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)