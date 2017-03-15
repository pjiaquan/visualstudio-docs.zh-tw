---
title: "CA1009：正確宣告事件處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1009：正確宣告事件處理常式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 處理公用或保護之事件的委派沒有正確的簽章、傳回型別或參數名稱。  
  
## 規則描述  
 事件處理常式方法會採用兩個參數。  第一個參數的型別為 <xref:System.Object?displayProperty=fullName> 且名稱為 'sender'。  這是引發事件的物件。  第二個參數的型別為 <xref:System.EventArgs?displayProperty=fullName> 且名稱為 'e'。  這是與事件相關聯的資料。  例如，若開啟檔案時即會引發事件，則事件資料通常會包含檔案名稱。  
  
 事件處理常式方法不應傳回值。  在 C\# 程式語言中，這是由傳回型別 `void` 所表示。  事件處理常式可在多個物件中叫用多個方法。  如果允許方法傳回值，則每個事件會產生多個傳回值，而且只能使用最後叫用之方法的值。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請更正委派的簽章、傳回型別或參數名稱。  如需詳細資訊，請參閱下列範例。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示適合處理事件的委派。  這個事件處理常式可叫用的方法符合在設計方針中所指定的簽章。  `AlarmEventHandler` 委派的型別名稱。  `AlarmEventArgs` 衍生自事件資料的基底類別 <xref:System.EventArgs>，並保留警示事件資料。  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## 相關規則  
 [CA2109：必須檢視可見的事件處理常式](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## 請參閱  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [NIB: Events and Delegates](http://msdn.microsoft.com/zh-tw/d98fd58b-fa4f-4598-8378-addf4355a115)