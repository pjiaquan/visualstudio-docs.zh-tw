---
title: "CA1402：避免在 COM 可見介面中多載 | Microsoft Docs"
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
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402：避免在 COM 可見介面中多載
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 元件物件模型 \(COM\) 可見的介面宣告了多載方法。  
  
## 規則描述  
 當多載方法會對 COM 用戶端公開 \(Expose\) 時，只有第一個方法多載會保留它的名稱。  後續的多載則會透過將名稱附加至底線字元 '\_' 和對應於多載宣告之順序的整數，重新命名為唯一的名稱。  例如，考慮下列方法。  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 這些方法會公開給 COM 用戶端，如下所示。  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Visual Basic 6 COM 用戶端無法藉由在名稱中使用底線的方式實作介面方法。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將多載方法重新命名，讓名稱是唯一的。  此外，利用下列方式讓該介面對 COM 而言是可見的：變更存取範圍為 `internal` \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 `Friend`\) 或是套用設定為 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 屬性 \(Attribute\)。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的介面和符合規則的介面。  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## 相關規則  
 [CA1413：避免在 COM 可見的實值類型中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407：避免在 COM 可見類型中使用靜態成員](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017：以 ComVisibleAttribute 標記組件](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 請參閱  
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)