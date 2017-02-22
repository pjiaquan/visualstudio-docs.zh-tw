---
title: "使用文字範本中的逸出序列 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, 逸出序列"
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 29
caps.handback.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 使用文字範本中的逸出序列
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在文字範本中使用逸出序列，來產生文字範本標記，以及 \(僅限 C\# 程式碼\) 逸出控制字元和引號。  
  
 若要將標準程式碼區塊的開頭和結尾標記列印到輸出檔，請依下列方式逸出標記：  
  
```  
\<# ... \#>  
```  
  
 您可以對其他文字範本指示詞和程式碼區塊標記執行相同的作業。  
  
 如果文字區塊包含用來逸出文字範本標記的字串，那麼您就可以使用下列逸出序列：  
  
-   如果文字範本標記前面有偶數個逸出 \(\\\) 字元，則範本分析器會將一半的逸出字元納入輸出，並加入該序列做為文字範本標記。  例如，如果文字範本中有四個逸出字元，產生的檔案中就會有兩個 "\\" 字元。  
  
-   如果文字範本標記前面有奇數個逸出 \(\\\) 字元，則範本分析器會將一半的 "\\" 字元加上標記本身 \(\<\# 或 \#\>\) 納入輸出，  但不會將該標記視為文字範本標記。  
  
-   如果逸出 \(\\\) 字元出現在任何其他序列中，除非它逸出控制字元或引號 \(僅限在 C\# 中\)，否則就會直接輸出該字元。  
  
## 請參閱  
 [如何：使用逸出序列從範本產生範本](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)