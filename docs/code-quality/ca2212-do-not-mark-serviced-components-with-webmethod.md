---
title: "CA2212：不要以 WebMethod 標記 Serviced 元件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2212：不要以 WebMethod 標記 Serviced 元件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|分類|Microsoft.Usage|  
|中斷變更|中斷|  
  
## 原因  
 型別中繼承自 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> 的方法是以 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> 標示。  
  
## 規則描述  
 <xref:System.Web.Services.WebMethodAttribute> 會套用到 XML Web Service 內使用 ASP.NET 所建立的方法，它會標示可以從遠端 Web 用戶端呼叫的方法。  方法和類別必須是公用的，並且在 ASP.NET Web 應用程式中執行。  <xref:System.EnterpriseServices.ServicedComponent> 型別是由 COM\+ 應用程式裝載，而且可以使用 COM\+ 服務。  因為不適用於相同案例，<xref:System.Web.Services.WebMethodAttribute> 不會套用至 <xref:System.EnterpriseServices.ServicedComponent> 型別。  尤其是將屬性 \(Attribute\) 加入到 <xref:System.EnterpriseServices.ServicedComponent> 方法，並不會使得方法可從遠端 Web 用戶端呼叫。  因為 <xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.EnterpriseServices.ServicedComponent> 方法具有衝突的內容和交易流程的行為及需求，所以方法的行為在某些情節中會是不正確的。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請從 <xref:System.EnterpriseServices.ServicedComponent> 方法中移除屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  沒有任何會正確組合這些項目的情節。  
  
## 請參閱  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>