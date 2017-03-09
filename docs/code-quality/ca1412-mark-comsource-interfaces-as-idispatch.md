---
title: "CA1412：將 ComSource 介面標記為 IDispatch | Microsoft Docs"
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
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412：將 ComSource 介面標記為 IDispatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 型別已標示為 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 屬性 \(Attribute\)，且至少有一個指定的介面未標示為已設定成 `InterfaceIsDispatch` 值的 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 屬性。  
  
## 規則描述  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 會用來識別類別公開給元件物件模型 \(COM\) 用戶端的事件介面。  這些介面會公開為 `InterfaceIsIDispatch`，以允許 Visual Basic 6 COM 用戶端接收事件告知。  依照預設，如果介面未標記為 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 屬性，則該介面會公開為雙重介面 \(Dual Interface\)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，可以加入或修改 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 屬性，讓所有已指定 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 屬性之介面的值可以設定為 InterfaceIsIDispatch。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示其中一個介面違反此規則的類別。  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## 相關規則  
 [CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## 請參閱  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/zh-tw/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)