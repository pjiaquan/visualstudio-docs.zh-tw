---
title: "CA2106：必須保護判斷提示 | Microsoft Docs"
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
  - "CA2106"
  - "SecureAsserts"
helpviewer_keywords: 
  - "CA2106"
  - "SecureAsserts"
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2106：必須保護判斷提示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SecureAsserts|  
|CheckId|CA2106|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 方法會判斷提示使用權限，而且不會在呼叫端上執行安全性檢查。  
  
## 規則描述  
 判斷提示安全性權限但未執行任何安全性檢查，會在您的程式碼中留下可能遭利用的安全性弱點。  判斷提示安全性權限之後，安全性堆疊查核行程 \(Stack Walk\) 會停止。  如果您會判斷提示使用權限但不會在呼叫端上執行任何檢查，則呼叫端可以利用您的使用權限間接執行程式碼。  只有當您確定判斷提示無法以有害的方式使用時，才能允許沒有安全性檢查的判斷提示。  如果您呼叫的程式碼無害，或使用者無法將任意資訊傳遞給您呼叫的程式碼，則判斷提示是無害的。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將安全性需求加入至方法或其宣告型別。  
  
## 隱藏警告的時機  
 只有在仔細檢閱安全性之後，才可以隱藏此規則的警告。  
  
## 請參閱  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)