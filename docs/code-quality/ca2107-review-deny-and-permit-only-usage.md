---
title: "CA2107：必須檢視 Deny 和 Permit Only 的使用方式 | Microsoft Docs"
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
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107：必須檢視 Deny 和 Permit Only 的使用方式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 方法會包含指定 PermitOnly 或 Deny 安全性動作的安全性檢查。  
  
## 規則描述  
 只有相當了解 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 安全性的人員才能執行 [Using the PermitOnly Method](http://msdn.microsoft.com/zh-tw/8c7bdb7f-882f-45b7-908c-6cbaa1767649) 和 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> 安全性動作。  而使用這些安全性動作的程式碼應該接受安全性檢閱。  
  
 Deny 會更改堆疊查核行程為了回應安全性需求而發生的預設行為。  不論呼叫堆疊中呼叫端的實際使用權限為何，它可以讓您指定在 Deny 方法期間絕對不能授與的使用權限。  如果堆疊查核行程偵測到受到 Deny 保護的方法，以及要求的使用權限已併入拒絕的使用權限中，則堆疊查核行程會失敗。  PermitOnly 也會更改堆疊查核行程的預設行為。  不論呼叫端的使用權限為何，它可以讓程式碼指定能夠授與的使用權限範圍。  如果堆疊查核行程偵測到受到 PermitOnly 保護的方法，以及要求的使用權限未併入 PermitOnly 所指定的使用權限中，則堆疊查核行程會失敗。  
  
 您應該仔細評估會依賴這些動作的程式碼，以找出因它有限用處和難以預測之行為所產生的安全性弱點。  請考慮下列事項：  
  
-   [Link Demands](../Topic/Link%20Demands.md)不會受到 Deny 或 PermitOnly 的影響。  
  
-   如果 Deny 或 PermitOnly 與導致堆疊查核行程的要求會出現在同一堆疊框架 \(Stack Frame\) 中，則安全性動作不會有任何作用。  
  
-   用於建構以路徑為基礎之使用權限的值通常可以利用多種方法指定。  拒絕存取某一形式的路徑，並不表示會拒絕存取所有形式的路徑。  例如，如果檔案共用對應至網路磁碟 X: 的 \\\\Server\\Share，若要拒絕存取共用上的檔案，則您必須拒絕 \\\\Server\\Share\\File、X:\\File，以及所有會存取檔案的路徑。  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> 可以在到達 Deny 或 PermitOnly 之前，終止堆疊查核行程。  
  
-   如果 Deny 有任何作用，也就是說，當呼叫端具有 Deny 封鎖的使用權限時，呼叫端可以略過 Deny 直接存取受保護的資源。  同樣地，如果呼叫端沒有拒絕的使用權限，則堆疊查核行程將會因為沒有 Deny 方法而失敗。  
  
## 如何修正違規  
 任何使用這些安全性動作都將導致違規。  若要修正違規，請勿使用這些安全性動作。  
  
## 隱藏警告的時機  
 只有在完成安全性檢閱後，才能隱藏這項規則的警告。  
  
## 範例  
 下列範例為 Deny 的某些限制。  
  
 下列程式庫包含一個類別，其中有兩個相同的方法，但保護它們的安全性要求卻不同。  
  
 [!CODE [FxCop.Security.PermitAndDeny#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny#1)]  
  
## 範例  
 下列應用程式會示範 Deny 對程式庫中受保護之方法所產生的作用。  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
 這個範例產生下列輸出。  
  
  **Demand：呼叫端的 Deny 對具有已判斷提示之使用權限的 Demand 沒有作用。**  
**LinkDemand：呼叫端的 Deny 對具有已判斷提示之使用權限的 LinkDemand 沒有作用。**  
**LinkDemand：呼叫端的 Deny 對 LinkDemand 保護的程式碼沒有作用。**  
**LinkDemand：這個 Deny 對 LinkDemand 保護的程式碼沒有作用。**   
## 請參閱  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/zh-tw/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/zh-tw/8c7bdb7f-882f-45b7-908c-6cbaa1767649)