---
title: "CA2117：APTCA 類型應該只擴充 APTCA 基底類型 | Microsoft Docs"
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
  - "CA2117"
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
helpviewer_keywords: 
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
  - "CA2117"
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2117：APTCA 類型應該只擴充 APTCA 基底類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 在具有 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 屬性 \(Attribute\) 之組件中之公用或保護的型別，會繼承自不具該屬性之組件中所宣告的型別。  
  
## 規則描述  
 根據預設，在具有強式名稱 \(Strong Name\) 的組件中，公用或保護的型別會受到完全信任所需的[Inheritance Demands](http://msdn.microsoft.com/zh-tw/28b9adbb-8f08-4f10-b856-dbf59eb932d9)隱含保護。  以 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) 屬性標記的強式名稱組件則沒有這種保護。  這個屬性會停用繼承要求。  這讓組件中所宣告的公開 \(Expose\) 型別可由不具有完全信任的型別繼承。  
  
 當完全受信任的組件中含有 APTCA 屬性，且組件中的型別會繼承自不允許部分信任之呼叫端的型別時，就可能會產生安全性弱點。  如果 `T1` 和 `T2` 這兩個型別會符合下列條件，則惡意的呼叫端可以使用型別 `T1`，略過保護 `T2` 的隱含完全信任繼承要求：  
  
-   `T1` 是具有 APTCA 屬性，且會在完全信任之組件中宣告的公用型別。  
  
-   `T1` 繼承自組件外部的型別 `T2`。  
  
-   `T2` 的組件不具有 APTCA 屬性，因此部分信任之組件中的型別不得繼承這個組件。  
  
 部分信任的型別 `X` 可以繼承自 `T1`，讓它可以存取 `T2` 中所宣告的繼承成員。  因為 `T2` 不具有 APTCA 屬性，所以它的直屬衍生型別 \(`T1`\) 必須滿足完全信任所需的繼承要求。`T1` 具有完全信任，因此可以通過這項檢查。  安全性的風險在於 `X` 並不能滿足可保護 `T2` 免於未受信任子類別化 \(Subclassing\) 的繼承要求。  基於這個原因，具有 APTCA 屬性的型別不得擴充不具這個屬性的型別。  
  
 另一個或許更為常見的安全性問題，在於衍生型別 \(`T1`\) 可以透過程式設計人員的錯誤，將需要完全信任之型別 \(`T2`\) 的公用成員公開。  發生這種情況時，未受信任的呼叫端將可以存取只有完全信任之型別才能取得的資訊。  
  
## 如何修正違規  
 如果回報為違規的型別位於不需要 APTCA 屬性的組件，請將該型別移除。  
  
 如果組件需要 APTCA 屬性，請將完全信任所需的繼承要求加入至型別，  以防止未受信任的型別進行繼承。  
  
 您也可以將 APTCA 屬性加入至報告的違規基底型別 \(Base Type\) 所在的組件，藉此修正違規。  如果未先針對組件中的所有程式碼或與組件相依之所有程式碼進行仔細的安全性檢視，則請勿採用此做法。  
  
## 隱藏警告的時機  
 若要放心地隱藏這項規則的警告，您必須確保型別所公開的公用成員未直接或間接地允許未受信任之呼叫端存取可能遭到惡意使用的機密資訊、作業或資源。  
  
## 範例  
 下列範例會使用兩個組件與一個測試應用程式，說明這項規則所偵測的安全性弱點。  第一個組件不具有 APTCA 屬性，因此不可由部分信任的型別 \(以前述的 `T2` 表示\) 繼承。  
  
 [!code-cs[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## 範例  
 第二個組件 \(以前述的 `T1` 表示\) 會受到完全信任，因此允許有部分信任的呼叫端。  
  
 [!CODE [FxCop.Security.YesAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit#1)]  
  
## 範例  
 測試型別 \(以前述的 `X` 表示\) 位於部分信任的組件中。  
  
 [!CODE [FxCop.Security.TestAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit#1)]  
  
 這個範例產生下列輸出。  
  
  **2003 年 2 月 22 日上午 12:00:00 在幽靜的山谷相會！**  
**測試答：陽光普照的草原**  
**2003 年 2 月 22 日上午 12:00:00 在陽光普照的草原相會！**   
## 相關規則  
 [CA2116：APTCA 方法應該只呼叫 APTCA 方法](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)  
  
## 請參閱  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/zh-tw/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Using Libraries from Partially Trusted Code](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Inheritance Demands](http://msdn.microsoft.com/zh-tw/28b9adbb-8f08-4f10-b856-dbf59eb932d9)