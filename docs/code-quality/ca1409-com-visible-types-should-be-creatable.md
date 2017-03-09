---
title: "CA1409：COM 可見類型應該是可建立的 | Microsoft Docs"
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
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409：COM 可見類型應該是可建立的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 特別標示為元件物件模型 \(Component Object Model，COM\) 可見的參考型別 \(Reference Type\) 包含公用參數化建構函式，但不包含公用預設 \(無參數\) 建構函式。  
  
## 規則描述  
 COM 用戶端無法建立沒有公用預設建構函式的型別。  不過，如果有其他方式可供建立型別並傳遞至用戶端 \(例如，透過方法呼叫的傳回值\)，則 COM 用戶端仍可存取該型別。  
  
 此規則會忽略自 <xref:System.Delegate?displayProperty=fullName> 衍生的型別。  
  
 根據預設，COM 可以看見下列各項：組件、公用型別、公用型別中的公用執行個體 \(Instance\) 成員，和公用實值型別的所有成員。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請新增公用預設建構函式 \(Constructor\)，或移除型別的 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>。  
  
## 隱藏警告的時機  
 如果有建立及傳遞物件至 COM 用戶端的其他方式，則您可以放心地隱藏這項規則的警告。  
  
## 相關規則  
 [CA1017：以 ComVisibleAttribute 標記組件](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 請參閱  
 [限定互通的 .NET 類型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)