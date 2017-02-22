---
title: "CA1502：避免過度複雜 | Microsoft Docs"
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
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1502：避免過度複雜
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|分類|Microsoft.Maintainability|  
|中斷變更|中斷|  
  
## 原因  
 方法的循環複雜度超過一般情況。  
  
## 規則描述  
 「*循環複雜度*」\(Cyclomatic Complexity\) 會測量整個方法中線性獨立路徑的數目，此數目是由條件分支的數目與複雜度決定。  較低的循環複雜度通常表示方法是易於了解、測試和維護。  循環複雜度是從方法的控制流程圖計算得出，它的公式如下：  
  
 循環複雜度 \= 邊緣數目 \- 節點數目 \+ 1  
  
 其中 node 表示邏輯分支點，edge 則表示 node 之間的線。  
  
 當循環複雜度超過 25 時，此規則會報告違規情形。  
  
 您可以進一步了解程式碼度量。請參考 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請重構方法以降低循環複雜度。  
  
## 隱藏警告的時機  
 如果無法輕易降低複雜度，而且方法也易於了解、測試和維護，則您可以放心地隱藏這項規則的警告。  包含大型 `switch` \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 `Select`\) 陳述式的方法尤其可以列為可排除的候選項目。  在開發週期晚期變動程式碼基底 \(Code Base\)，或是在先前送出之程式碼的執行階段行為中引入未預期的變更，這類的風險會比重構程式碼在維護方面所帶來的優點更加重要。  
  
## 循環複雜度的計算方式  
 循環複雜度是藉由在下列各項中加 1 來計算：  
  
-   分支數目 \(例如 `if`、`while` 和 `do`\)  
  
-   `switch` 中的 `case` 陳述式數目  
  
 下列範例顯示具有各種循環複雜度的方法。  
  
## 範例  
 **循環複雜度為 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## 範例  
 **循環複雜度為 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## 範例  
 **循環複雜度為 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## 範例  
 **循環複雜度為 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## 相關規則  
 [CA1501：避免過度繼承](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## 請參閱  
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)