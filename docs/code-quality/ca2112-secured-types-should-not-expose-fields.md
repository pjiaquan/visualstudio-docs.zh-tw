---
title: "CA2112：受保護類型不應公開欄位 | Microsoft Docs"
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
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
helpviewer_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2112：受保護類型不應公開欄位
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別包含公用欄位，而且由[Link Demands](../Topic/Link%20Demands.md)保護。  
  
## 規則描述  
 如果程式碼可存取受連結要求保護的型別執行個體，則程式碼不必滿足連結要求即可存取型別的欄位。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將欄位設成非公用，並加入傳回欄位資料的公用屬性或方法。  型別的 LinkDemand 安全性檢查會保護對型別之屬性和方法的存取。  但是，程式碼存取安全性不會套用在欄位。  
  
## 隱藏警告的時機  
 為了兼顧安全性問題以及理想的設計結果，建議您將公用欄位改為非公用欄位，以修正這些違規的情形。  如果欄位並未儲存應該繼續受保護的資訊，而您又不依賴欄位的內容，則可以隱藏這項規則的警告。  
  
## 範例  
 下列範例包含具有不安全欄位的程式庫型別 \(`SecuredTypeWithFields`\)、可以建立程式庫型別之執行個體而且會將執行個體誤傳給沒有權限建立執行個體之型別的型別 \(`Distributor`\)，以及即使沒有保護型別的權限但是仍然可以讀取執行個體欄位的應用程式程式碼。  
  
 下列程式庫程式碼會違反規則。  
  
 [!code-cs[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## 範例  
 因為連結要求會防護受保護型別，因此應用程式無法建立執行個體。  下列類別能夠讓應用程式取得受保護型別的執行個體。  
  
 [!CODE [FxCop.Security.LDOnFieldsDistributor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor#1)]  
  
## 範例  
 下列應用程式說明如果沒有存取受保護型別之方法的權限時，程式碼如何存取欄位。  
  
 [!code-cs[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
 這個範例產生下列輸出。  
  
  **建立 SecuredTypeWithFields 的執行個體。**  
**受保護型別欄位：22、33**  
**正在變更受保護型別的欄位...**  
**快取物件欄位：99、33**   
## 相關規則  
 [CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## 請參閱  
 [Link Demands](../Topic/Link%20Demands.md)   
 [資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)