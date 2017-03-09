---
title: "CA1711：識別項名稱不應該使用不正確的後置字元 | Microsoft Docs"
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
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711：識別項名稱不應該使用不正確的後置字元
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|類別|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 識別項的後置字元錯誤。  
  
## 規則描述  
 依照慣例，只有擴充特定基底型別 \(Base Type\) 或實作特定介面的型別名稱，或是從這些型別衍生的型別名稱，應以特定保留的後置字元結尾。  其他型別名稱不得使用這些保留的後置字元。  
  
 下表列出保留的後置字元和關聯的基底型別與介面。  
  
|後置字元|基底型別\/介面|  
|----------|--------------|  
|屬性|<xref:System.Attribute?displayProperty=fullName>|  
|Collection|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|事件處理常式委派|  
|例外狀況|<xref:System.Exception?displayProperty=fullName>|  
|使用權限|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|  
|堆疊|<xref:System.Collections.Stack?displayProperty=fullName>|  
|資料流|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 此外，**不**可使用下列後置字元：  
  
-   委派  
  
-   Enum  
  
-   Impl \- 請改用 'Core'  
  
-   Ex 或類似的後置字元，使其與相同型別較早的版本有所區別  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短新軟體程式庫的學習過程，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 請移除型別名稱的後置字元。  
  
## 隱藏警告的時機  
 除非在應用程式定義域中後置字元有明確的意義，否則請不要隨意隱藏這項規則的警告。  
  
## 相關規則  
 [CA1710：識別項應該使用正確的後置字元](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)  
  
## 請參閱  
 [屬性](../Topic/Attributes1.md)   
 [NIB: Events and Delegates](http://msdn.microsoft.com/zh-tw/d98fd58b-fa4f-4598-8378-addf4355a115)