---
title: "CA1702：複合字應該使用正確的大小寫 | Microsoft Docs"
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
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
helpviewer_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1702：複合字應該使用正確的大小寫
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|分類|Microsoft.Naming|  
|中斷變更|中斷 \- 在組件上引發時。<br /><br /> 非中斷 \- 在型別參數上引發時。|  
  
## 原因  
 識別項的名稱包含多個單字，而其中至少有一個單字是大小寫不正確的複合字。  
  
## 規則描述  
 識別項的名稱可依大小寫分成多個字。  連續兩個字的每個組合都由 Microsoft 拼字檢查程式庫進行檢查。  如果可以辨識，識別項便會產生規則違規。  導致違規的複合字範例包括 "CheckSum" 和 "MultiPart"，其大小寫應分別為 "Checksum" 和 "Multipart"。  由於先前的通用使用方式，某些例外狀況會內建在規則中，而且有些單一的字會加上旗標，例如 "Toolbar" 和 "Filename"，而這些字的大小寫應該是區分了兩個不同的字 \(在此範例中是 "ToolBar" 和 "FileName"\)。  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短新軟體程式庫的學習過程，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 請將名稱變更為正確的大小寫。  
  
## 隱藏警告的時機  
 如果拼字字典可以辨識複合字的兩個部分，而其原意就是要使用兩個字，則可以放心地隱藏這項規則的警告。  
  
## 相關規則  
 [CA1701：資源字串複合字應該使用正確的大小寫](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## 請參閱  
 [命名方針](../Topic/Naming%20Guidelines.md)   
 [大小寫慣例](../Topic/Capitalization%20Conventions.md)