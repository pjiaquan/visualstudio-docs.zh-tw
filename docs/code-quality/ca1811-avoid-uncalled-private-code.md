---
title: "CA1811：避免使用未呼叫的私用程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1811：避免使用未呼叫的私用程式碼
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 private 或 internal \(組件層級\) 成員在組件中沒有呼叫端，不會由 Common Language Runtime 叫用，而且委派也未叫用該成員。  此規則不會檢查下列成員：  
  
-   明確介面成員  
  
-   靜態建構函式  
  
-   序列化 \(Serialization\) 建構函式  
  
-   以 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 標示的方法  
  
-   做為覆寫的成員  
  
## 規則描述  
 如果出現規則邏輯目前未識別的進入點 \(Entry Point\)，此規則會產生誤報。  此外，編譯器可能將不可呼叫的程式碼發出到組件中。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除不可呼叫的程式碼，或加入可呼叫該程式碼的程式碼。  
  
## 隱藏警告的時機  
 您可以放心地隱藏這項規則的警告。  
  
## 相關規則  
 [CA1812：避免使用未執行個體化的內部類別](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801：必須檢視未使用的參數](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)