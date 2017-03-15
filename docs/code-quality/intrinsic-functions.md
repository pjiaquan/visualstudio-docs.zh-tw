---
title: "內建函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_String_length_"
  - "_Param_"
  - "_Curr_"
  - "_Old_"
  - "_Nullterm_length_"
  - "_Inexpressible_"
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 內建函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 SAL 的運算式可以是 C \+\+. \/C 運算式，而則是沒有邊效果 \(例如， C\+\+ 的運算式條件下，\-\-和函式呼叫都具有副作用在此內容中。不過， SAL 提供可用來 SAL 運算式的一些類似函式的物件和某些保留的符號。  這些稱為 *內建函式*。  
  
## 一般目的。  
 下列 instrinsic 函式附註提供一般公用程式為 SAL 使用。  
  
|註釋|說明|  
|--------|--------|  
|`_Curr_`|目前標註物件的同義字。當 `_At_` 附註仍在使用中時，`_Curr_` 和第一個參數一樣指向 `_At_` 。否則就是參數或附註語彙關係的整個函式的傳回值。|  
|`_Inexpressible_(expr)`|用來表示緩衝區的大小太複雜而無法以標記法表示的情況，例如，當透過掃描輸入資料集和計數中選取成員的計算。|  
|`_Nullterm_length_(param)`|`param` 是元素數目緩衝區的等號 \(但不包含 null 結束字元\)。  它也可以套用至非彙總，非 void 型別所有緩衝區。|  
|`_Old_(expr)`|在評估前置條件， `_Old_` 傳回輸入值 `expr`。在評估後狀況，則傳回值 `expr` ，因為它在前置條件會評估。|  
|`_Param_(n)`|函式的第 `n`參數計數，從 1 到 `n`和 `n` 是常值整數常數。  如果參數名稱為，這個附註與名稱存取參數相同。 **Note:**  `n` 可能代表省略符號定義的位置參數或在不使用名稱的函式原型 \(Prototype\)。|  
|`return`|C\/C\+\+ 保留的關鍵字 `return` 可用於 SAL 運算式表示函式的傳回值。值只能在張貼狀態，因此，它是使用其語法錯誤會發生在之前的狀態。|  
  
## 特定字串  
 下列內建函式附註可讓資料的作業。  這四種函式符合同一個目的:傳回型別的項目數目 null 結束字元之前找到的。  差異在於這種所參考的項目的資料。  請注意，如果您要指定由字元所組成 null 結尾緩衝區的長度，請使用本節中的 `_Nullterm_length_(param)` 標記法。  
  
|註釋|說明|  
|--------|--------|  
|`_String_length_(param)`|`param`是不包含null terminator的緩衝區的元件數目。  這個標記法為字串型別字元是保留的名稱。|  
|`strlen(param)`|`param`是不包含null terminator的緩衝區的元件數目。  這個標記法是保留為字元陣列，會使用和 C 執行階段函式相似的 [strlen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)。|  
|`wcslen(param)`|`param`是不包含null terminator的緩衝區的元件數目。  這個標記法是保留為寬字元陣列，會使用和 C 執行階段函式相似的 [wcslen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)。|  
  
## 請參閱  
 [使用 SAL 註釋減少 C\/C\+\+ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [最佳作法和範例](../code-quality/best-practices-and-examples-sal.md)