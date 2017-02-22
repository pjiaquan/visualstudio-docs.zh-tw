---
title: "CA1309：使用循序的 StringComparison | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1309：使用循序的 StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|分類|Microsoft.Globalization|  
|中斷變更|中斷|  
  
## 原因  
 非語言的字串比較作業未將 <xref:System.StringComparison> 參數設定為 **Ordinal** 或 **OrdinalIgnoreCase**。  
  
## 規則描述  
 許多字串作業 \(最重要的是 <xref:System.String.Compare%2A?displayProperty=fullName> 和 <xref:System.String.Equals%2A?displayProperty=fullName> 方法\) 現在都提供接受 <xref:System.StringComparision?displayProperty=fullName> 列舉值做為參數的多載。  
  
 當您指定 **StringComparison.Ordinal** 或 **StringComparison.OrdinalIgnoreCase** 時，字串比較將是非語言性質。  也就是說，在決定比較結果時，會忽略自然語言專有的功能。  這表示結果是根據比較簡單的位元組而決定，並忽略依照文化特性所參數化之大小寫或對等的表格。  因此，藉由明確地將參數設定為 **StringComparison.Ordinal** 或 **StringComparison.OrdinalIgnoreCase**，您的程式碼通常會在速度和正確性方面獲得提升，並且更加可靠。  
  
## 如何修正違規  
 若要修正這個規則的違規情形，請將字串比較方法變更為接受 <xref:System.StringComparison?displayProperty=fullName> 列舉做為參數的多載，並指定 **Ordinal** 或 **OrdinalIgnoreCase**。  例如，將 `String.Compare(str1, str2)` 變更為 `String.Compare(str1, str2, StringComparison.Ordinal)`。  
  
## 隱藏警告的時機  
 當程式庫或應用程式適用於有限制的地區設定使用者，或者應使用目前文化特性的語意時，您可以放心地隱藏此規則的警告。  
  
## 請參閱  
 [全球化警告](../code-quality/globalization-warnings.md)   
 [CA1307：指定 StringComparison](../code-quality/ca1307-specify-stringcomparison.md)