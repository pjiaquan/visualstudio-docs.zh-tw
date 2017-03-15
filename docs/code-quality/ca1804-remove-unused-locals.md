---
title: "CA1804：必須移除未使用的區域變數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1804：必須移除未使用的區域變數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|RemoveUnusedLocals|  
|CheckId|CA1804|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 方法會宣告區域變數，但除了可能會做為指派陳述式 \(Assignment Statement\) 的收件者之外，並未使用該變數。  如果要以此規則進行分析，則測試的組件 \(Assembly\) 必須建有偵錯資訊，而且還可以使用相關的程式資料庫 \(.pdb\) 檔案。  
  
## 規則描述  
 未使用的區域變數和不必要的設定，會增加組件的大小並降低效能。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除或使用區域變數。  請注意，當 `optimize` 選項啟用時，[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 中隨附的 C\# 編譯器會移除未使用的區域變數。  
  
## 隱藏警告的時機  
 如果變數是由編譯器發出，請隱藏這項規則的警告。  如果效能和程式碼維護不是主要考量，則您可以放心地隱藏此規則的警告或停用該規則。  
  
## 範例  
 在下列範例中，程式碼會顯示多個未使用的區域變數。  
  
 [!CODE [FxCop.Performance.UnusedLocals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals#1)]  
  
## 相關規則  
 [CA1809：避免使用過多區域變數](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811：避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812：避免使用未執行個體化的內部類別](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801：必須檢視未使用的參數](../Topic/CA1801:%20Review%20unused%20parameters.md)