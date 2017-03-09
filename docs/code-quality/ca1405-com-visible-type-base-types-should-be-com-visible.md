---
title: "CA1405：COM 可見類型的基底類型應該是 COM 可見 | Microsoft Docs"
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
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405：COM 可見類型的基底類型應該是 COM 可見
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|分類|Microsoft.Interoperability|  
|中斷變更|DependsOnFix|  
  
## 原因  
 元件物件模型 \(COM\) 可見的型別衍生自非 COM 可見的型別。  
  
## 規則描述  
 當 COM 可見型別在新版本中加入成員時，它必須遵守嚴格的方針，以免中斷繫結至目前版本的 COM 用戶端。  COM 不可見的型別假設在加入新成員時不必遵循這些 COM 版本控制規則。  但是，如果 COM 可見型別衍生自 COM 不可見的型別，並且公開 \(Expose\) <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ClassInterfaceType> \(預設值\) 的類別介面，則基底型別的所有公用成員 \(除非這些公用成員特別標記為 COM 不可見，這可能會是多餘的\) 都會公開至 COM。  如果基底型別在後來的版本中加入新成員，則可能會中斷繫結至衍生型別之類別介面的任何 COM 用戶端。  COM 可見型別應該只會衍生自 COM 可見型別，以減少中斷 COM 用戶端的可能性。  
  
## 如何修正違規  
 若要修正這項規則的違規情形，請使基底型別成為 COM 可見的或使衍生型別成為 COM 不可見的。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例顯示違反規則的型別。  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/zh-tw/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)