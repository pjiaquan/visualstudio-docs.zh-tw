---
title: "CA1020：避免在命名空間中包含過少的類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1020"
  - "AvoidNamespacesWithFewTypes"
helpviewer_keywords: 
  - "AvoidNamespacesWithFewTypes"
  - "CA1020"
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1020：避免在命名空間中包含過少的類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 非全域命名空間的命名空間包含的型別少於五個。  
  
## 規則描述  
 請確定每個命名空間都有邏輯組織，而且有合理的原因可以將型別置於以疏鬆方式填入的命名空間中。  命名空間應包含一起用於大部分案例中的型別。  當應用程式為互斥 \(Mutually Exclusive\) 時，型別應該位於不同的命名空間中。  例如，<xref:System.Web.UI> 命名空間包含用於 Web 應用程式中的型別，而 <xref:System.Windows.Forms> 命名空間則包含用於 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 架構應用程式中的型別。  雖然這兩個命名空間具有控制使用者介面外觀的型別，這些型別沒有設計用於相同的應用程式。  因此，它們位於不同的命名空間。  嚴謹的命名空間組織可以增加功能的探索能力，所以也是很有幫助的。  藉由檢查命名空間階層，程式庫消費者應能夠找出會實作功能的型別。  
  
> [!NOTE]
>  不可以將設計階段型別和使用權限合併到其他的命名空間，以符合此方針。  這些型別屬於自己的命名空間 \(低於您的主要命名空間\)，而且命名空間應該分別以 `.Design` 和 `.Permissions` 做為結尾。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請嘗試將包含少數型別的命名空間合併成單一命名空間。  
  
## 隱藏警告的時機  
 如果命名空間不包含與其他命名空間中型別一起使用的型別，則您可以放心地隱藏這項規則的警告。