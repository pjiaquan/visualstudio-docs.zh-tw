---
title: "CA2114：方法安全性應該是類型的超集 | Microsoft Docs"
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
  - "MethodSecurityShouldBeASupersetOfType"
  - "CA2114"
helpviewer_keywords: 
  - "CA2114"
  - "MethodSecurityShouldBeASupersetOfType"
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2114：方法安全性應該是類型的超集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 型別具有宣告式安全性而且其中一個方法具有相同安全性動作的宣告式安全性，以及不是[Link Demands](../Topic/Link%20Demands.md)或[Inheritance Demands](http://msdn.microsoft.com/zh-tw/28b9adbb-8f08-4f10-b856-dbf59eb932d9)的安全性動作，而且型別所檢查的使用權限不是方法所檢查的使用權限子集。  
  
## 規則描述  
 方法不應該同時具有相同動作的方法層級和型別層級宣告式安全性。  這兩個檢查不會合併，只會套用方法層級要求。  例如，如果型別要求使用權限 `X`，而且它的其中一個方法要求使用權限 `Y`，則程式碼不需要使用權限 `X` 即可執行方法。  
  
## 如何修正違規  
 請檢閱您的程式碼，確定需要這兩個動作。  如果需要這兩個動作，則請確定方法層級動作會包括在型別層級中指定的安全性。  例如，如果型別要求使用權限 `X`，而且它的方法也需要求使用權限 `Y`，則方法應該明確地要求 `X` 和 `Y`。  
  
## 隱藏警告的時機  
 如果方法不需要型別所指定的安全性，則您可以放心地隱藏這項規則的警告。  但是，這不是一般案例，而且可能會需要仔細地檢閱設計。  
  
## 範例  
 下列範例會使用環境使用權限，示範違反這項規則的危險性。  在這個範例中，應用程式程式碼會在拒絕型別所需的使用權限之前，建立安全型別的執行個體。  在真實的威脅案例中，應用程式會需要另一種取得物件執行個體的方法。  
  
 在下列範例中，程式庫會要求型別的寫入權限和方法的讀取權限。  
  
 [!code-cs[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## 範例  
 即使方法不符合型別層級安全性要求，下列應用程式程式碼也會呼叫這個方法，示範程式庫的弱點。  
  
 [!code-cs[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 這個範例產生下列輸出。  
  
  **\[所有使用權限\] 個人資訊: 6\/16\/1964 12:00: 00 AM \[沒有寫入權限 \(被型別所要求\)\] 個人資訊: 6\/16\/1964 12:00: 00 AM \[沒有讀取權限\(被方法所要求\)\] 無法存取個人資訊: 要求失敗。**   
## 請參閱  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/zh-tw/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)