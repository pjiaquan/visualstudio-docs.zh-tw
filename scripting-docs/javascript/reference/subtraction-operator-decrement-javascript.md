---
title: "減法運算子 (-) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "-"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "- 運算子"
  - "- 運算子, 關於 - 運算子"
  - "算術運算子, 減法"
  - "negation 運算子"
  - "運算子, 減法"
  - "減法運算子, 語法"
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 減法運算子 (-) (JavaScript)
將某運算式的值減去另一運算式的值，或是提供單一運算式的一元負值。  
  
## 語法  
  
```  
  
result = number1 - number2;  
  
```  
  
## 參數  
 *result*  
 任意數值變數。  
  
 `number`  
 任何數值運算式。  
  
 `number1`  
 任何數值運算式。  
  
 `number2`  
 任何數值運算式。  
  
## 備註  
 在語法 1 中，**\-** 運算子是用來尋找兩個數字間差異的算術減法運算子。  在語法 2 中，**\-** 運算子是用來表示運算式負值的一元負運算子。  
  
 對語法 2 而言，運算式會針對所有一元運算子使用下列方式評估：  
  
-   如果套用到未定義或 `null` 運算式，則會發生執行階段錯誤。  
  
-   物件會轉換成字串。  
  
-   如果可能的話，字串會轉換成數字。  如果不行，就會發生執行階段錯誤。  
  
-   布林值會被當做數字處理 \(如果為 false 則是 0，為 true 則是 1\)。  
  
 接著，這個運算子會套用到產生的數字。  在語法 2 中，如果產生的數字是非零值，則 *result* 等於產生的數字加上它的反向正負號。  如果產生的數字是零，則 *result* 為零。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [減法設定運算子 \(\-\=\)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)