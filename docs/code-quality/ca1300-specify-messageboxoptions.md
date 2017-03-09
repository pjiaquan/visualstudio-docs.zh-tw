---
title: "CA1300：指定 MessageBoxOptions | Microsoft Docs"
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
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300：指定 MessageBoxOptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|分類|Microsoft.Globalization|  
|中斷變更|中斷|  
  
## 原因  
 方法會呼叫 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 方法 \(不使用 <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> 引數\) 的多載。  
  
## 規則描述  
 若要對使用由右至左讀取順序的文化特性 \(Culture\) 正確顯示訊息方塊，<xref:System.Windows.Forms.MessageBoxOptions> 列舉的 <xref:System.Windows.Forms.MessageBoxOptions> 和 <xref:System.Windows.Forms.MessageBoxOptions> 成員必須傳遞至 <xref:System.Windows.Forms.MessageBox.Show%2A> 方法。  檢視包含控制項的 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> 屬性，以判斷是否使用由右至左的讀取順序。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請呼叫 <xref:System.Windows.Forms.MessageBox.Show%2A> 方法的多載，而這個方法會採用 <xref:System.Windows.Forms.MessageBoxOptions> 引數。  
  
## 隱藏警告的時機  
 當使用由右至左讀取順序的文化特性不會將程式碼程式庫當地語系化時，您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例顯示方法，該方法顯示具有適用於文化特性讀取順序選項的訊息方塊。  建置 \(Build\) 範例時需要資源檔 \(未顯示\)。  遵循範例中的註解以在不使用資源檔的狀況下建置範例，並測試由右至左功能。  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## 請參閱  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [桌面應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)