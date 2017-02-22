---
title: "CA1307：指定 StringComparison | Microsoft Docs"
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
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1307：指定 StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SpecifyStringComparison|  
|CheckId|CA1307|  
|分類|Microsoft.Globalization|  
|中斷變更|中斷|  
  
## 原因  
 字串比較作業會使用未設定 <xref:System.StringComparison> 參數的方法多載。  
  
## 規則描述  
 許多字串作業 \(最重要的是 <xref:System.String.Compare%2A> 和 <xref:System.String.Equals%2A> 方法\) 可提供接受 <xref:System.StringComparison> 列舉值做為參數的多載。  
  
 當接受 <xref:System.StringComparison> 參數的多載存在時，就應該使用這個多載，而非使用不接受此參數的多載。  藉由明確設定這個參數，您的程式碼通常會較清楚且較容易維護。  
  
## 如何修正違規  
 若要修正這個規則的違規情形，請將字串比較方法變更為接受 <xref:System.StringComparison> 列舉做為參數的多載。  例如，將 `String.Compare(str1, str2)` 變更為 `String.Compare(str1, str2, StringComparison.Ordinal)`。  
  
## 隱藏警告的時機  
 當程式庫或應用程式適用於有限制的地區設定使用者，並且將因此未進行當地語系化時，您可以放心地隱藏此規則的警告。  
  
## 請參閱  
 [全球化警告](../code-quality/globalization-warnings.md)   
 [CA1309：使用循序的 StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)