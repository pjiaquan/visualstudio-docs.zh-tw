---
title: "CA1059：成員不應該公開特定的具象類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
helpviewer_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1059：成員不應該公開特定的具象類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的成員是特定的具象型別，或者會透過它的其中一個參數或傳回值公開特定的具象型別。  此規則目前會報告下列具象型別的公開：  
  
-   衍生自 <xref:System.Xml.XmlNode?displayProperty=fullName> 的型別。  
  
## 規則描述  
 具象型別就是具有完整實作 \(Implementation\) 且因此能加以具現化 \(Instantiated\) 的型別。  若要讓成員能廣泛使用，請使用建議的介面取代具象型別。  如此可讓成員接受任何會實作此介面的型別，或是用於預期要有實作介面之型別的地方。  
  
 下表會列出目標具象型別及其建議的取代介面。  
  
|具象型別|取代型|  
|----------|---------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> 使用此介面以減少 XML 資料來源之特定實作的成員|  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將具象型別變更為建議的介面。  
  
## 隱藏警告的時機  
 如果必須由具象型別提供特定功能，則您可以放心地隱藏此規則的訊息。  
  
## 相關規則  
 [CA1011：建議將基底類型當做參數傳遞](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)