---
title: "CA2108：必須檢查實值類型上的宣告式安全性 | Microsoft Docs"
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
  - "ReviewDeclarativeSecurityOnValueTypes"
  - "CA2108"
helpviewer_keywords: 
  - "CA2108"
  - "ReviewDeclarativeSecurityOnValueTypes"
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2108：必須檢查實值類型上的宣告式安全性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|分類|Microsoft.Security|  
|中斷變更|不中斷|  
  
## 原因  
 公用或保護的實值型別 \(Value Type\) 會受到[資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)或[Link Demands](../Topic/Link%20Demands.md)的保護。  
  
## 規則描述  
 在執行其他建構函式 \(Constructor\) 之前，會以預設的建構函式配置並初始化實值型別。  如果實值型別受到 Demand 或 LinkDemand 的保護，且呼叫端不具備可以滿足安全性檢查的使用權限，則預設建構函式以外的建構函式將會失敗，並擲回例外狀況。  此時無法取消實值型別的配置，它將保持在預設建構函式所設定的狀態。  請勿假設會傳遞實值型別執行個體的呼叫端具有建立或存取執行個體的使用權限。  
  
## 如何修正違規  
 除非從型別移除安全性檢查並使用方法層級的安全性檢查，否則無法修正此規則的違規情形。  請注意，以這種方式修正違規並無法防止不具適當使用權限之呼叫端取得實值型別的執行個體。  您必須確保實值型別的執行個體在預設狀態下不會公開 \(Expose\) 敏感性資訊，且不會用於有害的用途。  
  
## 隱藏警告的時機  
 如果呼叫端在預設狀態下可以取得實值型別的執行個體，而且不會造成安全性威脅，則可以隱藏此規則的警告。  
  
## 範例  
 在下列範例中，程式碼會顯示因包含實值型別而違反此規則的程式庫。  請注意，`StructureManager` 型別會假設傳遞實值型別執行個體的呼叫端具有建立或存取執行個體的使用權限。  
  
 [!code-cs[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## 範例  
 下列應用程式會示範程式庫的弱點。  
  
 [!code-cs[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 這個範例產生下列輸出。  
  
  **結構自訂建構函式：要求失敗。**  
**新的值 SecuredTypeStructure 100 100**  
**新的值 SecuredTypeStructure 200 200**   
## 請參閱  
 [Link Demands](../Topic/Link%20Demands.md)   
 [資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)