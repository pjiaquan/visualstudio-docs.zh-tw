---
title: "指定套用註釋的時機和位置 | Microsoft Docs"
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
  - "_Group_"
  - "_At_"
  - "_When_"
  - "_At_buffer_"
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 指定套用註釋的時機和位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在註解是條件式時，可能需要其他標記法指定到該分析器。例如，如果有函式可以是同步或非同步的變數，函式的行為如下:在同步處理案例它永遠是最後成功，但是如果無法立即成功，在非同步案例就會回報錯誤。  當函式在同步處理期間呼叫保存時，結果值會檢查而不提供值給程式碼分析器，因為它不會被傳回。不過，當函式非同步呼叫，且函式結果不檢查，則會發生嚴重的錯誤。  這個範例說明您可以在這個中後註釋描述的 `_When_` 文件啟用檢查的情況。  
  
## 結構化的註釋  
 若要控制附註的位置和時間，請使用以下附註描述的結構。  
  
|註釋|說明|  
|--------|--------|  
|`_At_(expr, anno-list)`|`expr` 是產生左值的運算式。  在 `anno-list` 的附註套用至由 `expr`命名的物件。  對於的每個 `anno-list`， `expr` 附註，如果附註解譯在前置條件、後置狀況會說明，加上狀況解譯。|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` 是產生左值的運算式。  在 `anno-list` 的附註套用至由 `expr`命名的物件。  對於的每個 `anno-list`， `expr` 附註，如果附註解譯在前置條件、後置狀況會說明，加上狀況解譯。<br /><br /> `iter` 是變數名稱的範圍限定 \(包含 `anno-list`\)。  `iter` 具有隱含型別 `long`。  在任何封閉範圍中的同名變數是被評估為隱藏。<br /><br /> `elem-count` 是計算結果為整數的運算式。|  
|`_Group_(anno-list)`|在 `anno-list` 的附註都會被視為具有套用至群組、至每個附註的所有限定詞。|  
|`_When_(expr, anno-list)`|`expr` 是可以轉換成 `bool`的運算式。  在非零值時 \(`true`\) 在 `anno-list` 指定的附註視為適用。<br /><br /> 根據預設，在 `anno-list`的註解， `expr` 會解譯使用輸入值，如果標記法是前置條件；如果標記法是後狀況，則會使用輸出值。  若要覆寫預設值， `_Old_` 內部可在評估狀況後使用輸入值。 **Note:**  不同的附註可做為 `_When_` 的結果使用，如果變數的值 \(例如， `*pLength`\) 因為評估在前置條件的 `expr` 結果與緊接在狀況衍生的不同。|  
  
## 請參閱  
 [使用 SAL 註釋減少 C\/C\+\+ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [內建函式](../code-quality/intrinsic-functions.md)   
 [最佳作法和範例](../code-quality/best-practices-and-examples-sal.md)