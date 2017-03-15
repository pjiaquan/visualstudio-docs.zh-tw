---
title: "DA0006：覆寫實值類型的 Equals() | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAOverrideEquals"
  - "vs.performance.6"
  - "vs.performance.DA0006"
  - "vs.performance.rules.DA0006"
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0006：覆寫實值類型的 Equals()
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0006|  
|分類|.NET Framework 使用|  
|程式碼剖析方法|取樣|  
|Message|覆寫實值型別的 Equals 和等號比較運算子。|  
|訊息類型|警告|  
  
## 原因  
 Equals 方法的呼叫，或是公用實值型別的相等運算子，佔有程式碼剖析資料的一大部分。  請考慮實作更有效率的方法。  
  
## 規則描述  
 對於實值型別而言，Equals 的繼承實作會使用 <xref:System.Reflection> 程式庫，並比較型別中所有欄位的內容。  但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。  如果預期使用者會比較或排序執行個體，或是使用執行個體做為雜湊資料表索引鍵，則您的實值型別應該實作 Equals。  如果您的程式語言支援運算子多載，那麼還需要提供等號比較運算子和不等比較運算子的實作。  
  
 如需如何覆寫 Equals 和相等運算子的詳細資訊，請參閱[實作 Equals 和相等運算子 \(\= \=\) 的方針](http://go.microsoft.com/fwlink/?LinkId=177818)。  
  
## 如何調查警告  
 如需實作 Equals 和相等運算子的範例，請參閱程式碼分析規則 [CA1815：覆寫實值類型上的等號和等號比較運算子](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)