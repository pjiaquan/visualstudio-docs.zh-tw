---
title: "CA1408：不要使用 AutoDual ClassInterfaceType | Microsoft Docs"
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
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408：不要使用 AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 元件物件模型 \(COM\) 可見的型別是以設定為 <xref:System.Runtime.InteropServices.ClassInterfaceType> 的 `AutoDual` 值的 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性所標記。  
  
## 規則描述  
 使用雙重介面 \(Dual Interface\) 的型別可讓用戶端繫結至特定的介面配置。  在未來版本中，若型別或任何基底型別 \(Base Type\) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。  依照預設，如果未指定 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性，則會使用分派介面。  
  
 除非已標記，否則所有公用的非泛型型別對 COM 皆為可見的，而所有非公用的泛型型別對 COM 則皆不可見的。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性的值變更為 <xref:System.Runtime.InteropServices.ClassInterfaceType> 的 `None` 值，並明確地定義此介面。  
  
## 隱藏警告的時機  
 除非確定型別及其基底型別的配置在未來版本中不會變更，否則請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反此規則的類別，並重新宣告類別以便使用明確的介面。  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## 相關規則  
 [CA1403：自動配置類型不應該是 COM 可見](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412：將 ComSource 介面標記為 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## 請參閱  
 [Introducing the Class Interface](http://msdn.microsoft.com/zh-tw/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [限定互通的 .NET 類型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)