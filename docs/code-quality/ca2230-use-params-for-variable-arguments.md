---
title: "CA2230：必須使用 params 做為變數引數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230：必須使用 params 做為變數引數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|分類|Microsoft.Usage|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別包含使用 `VarArgs` 呼叫慣例 \(Calling Convention\) 之公用或保護的方法。  
  
## 規則描述  
 `VarArgs` 呼叫慣例會和採用可變參數數目的某些方法定義一起使用。  使用 `VarArgs` 呼叫慣例的方法不符合 Common Language Specification \(CLS\) 標準，且無法跨程式語言存取。  
  
 在 C\# 中，當方法的參數清單以 `__arglist` 關鍵字結尾時，就會使用 `VarArgs` 呼叫慣例。  Visual Basic 不支援 `VarArgs` 呼叫慣例，而 Visual C\+\+ 只允許在使用省略符號 `...` 標記法的 Unmanaged 程式碼中使用此慣例。  
  
## 如何修正違規  
 若要在 C\# 中修正此規則的違規情形，請改用 [params](/dotnet/csharp/language-reference/keywords/params) 關鍵字，而非 `__arglist`。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示兩個方法，其中一個違反規則，而另一個符合規則。  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## 請參閱  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)