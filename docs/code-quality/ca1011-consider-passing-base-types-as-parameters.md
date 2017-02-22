---
title: "CA1011：建議將基底類型當做參數傳遞 | Microsoft Docs"
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
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1011：建議將基底類型當做參數傳遞
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 方法宣告中包含屬於衍生型別 \(Derived Type\) 的型式參數，但該方法只會呼叫該參數的基底型別 \(Base Type\) 成員。  
  
## 規則描述  
 當方法宣告將基底型別指定為參數，則從此基底型別衍生的任何型別都可以當做對應引數傳遞給方法。  在方法主體內使用引數時，執行的特定方法需視引數型別而定。  如果不需要以衍生型別提供額外的功能，則可以使用基底型別讓方法獲得更廣泛的使用。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將參數型別變更為基底型別。  
  
## 隱藏警告的時機  
 您可以放心地隱藏這項規則的警告。  
  
-   如果方法需要衍生型別所提供的特定功能  
  
     \-或\-  
  
-   強制只能將衍生型別或衍生程度更大的型別傳遞至方法。  
  
 在這些情況下，因為編譯器和執行階段提供了強式型別檢查，程式碼將會變得更強固。  
  
## 範例  
 在下列範例中，程式碼會顯示方法 `ManipulateFileStream`，它僅可與違反此規則的 <xref:System.IO.FileStream> 物件一起使用。  第二個方法 `ManipulateAnyStream` 會以 <xref:System.IO.Stream> 取代 <xref:System.IO.FileStream> 參數，以滿足此規則。  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## 相關規則  
 [CA1059：成員不應該公開特定的具象類型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)