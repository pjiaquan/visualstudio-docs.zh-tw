---
title: "CA2130：安全性關鍵常數應該是透明的 | Microsoft Docs"
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
  - "CA2130"
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2130：安全性關鍵常數應該是透明的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 常數欄位或列舉成員會標示 <xref:System.Security.SecurityCriticalAttribute>。  
  
## 規則描述  
 因為編譯器內嵌常數的值，所以沒有針對常數值強制透明度，因此在執行階段不需要查詢。  常數欄位應該具備安全性透明，程式碼檢閱者才不會假設透明程式碼無法存取常數。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除欄位或値的 SecurityCritical 屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 在下列範例中，列舉值 `EnumWithCriticalValues.CriticalEnumValue` 與常數 `CriticalConstant` 會引發這項警告。  若要修正此問題，請移除 \[`SecurityCritical`\] 屬性，使它們具備安全性透明。  
  
 [!code-cs[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]