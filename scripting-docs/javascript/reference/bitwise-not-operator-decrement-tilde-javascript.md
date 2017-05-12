---
title: "位元 NOT 運算子 (~) (JavaScript) | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "位元運算子, NOT 運算子"
  - "NOT 運算子"
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 位元 NOT 運算子 (~) (JavaScript)
針對運算式執行位元 NOT \(否定\) 運算。  
  
## 語法  
  
```  
  
result = ~ expression  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression*  
 任何運算式。  
  
## 備註  
 所有的一元運算子 \(如 `~` 運算子\) 都會依照下列方式評估運算式：  
  
-   如果套用到未定義或 `null` 運算式，則會發生執行階段錯誤。  
  
-   物件會轉換成字串。  
  
-   如果可能的話，字串會轉換成數字。  如果不行，就會發生執行階段錯誤。  
  
-   布林值會被當做數字處理 \(如果為 false 則是 0，為 true 則是 1\)。  
  
 接著，這個運算子會套用到產生的數字。  
  
 `~` 運算子會先查看運算式值的二進位表示，然後針對該值執行位元否定運算。  
  
 任何在運算式中為 1 的數字，在結果中就變成 0。  任何在運算式中為 0 的數字，在結果中就變成 1。  
  
 下列範例說明如何使用位元 NOT \(~\) 運算子。  
  
```  
var temp = ~5;  
```  
  
 產生的值是 \-6，如下表所示。  
  
|運算式|二進位值 \(二的補數\)|十進位值|  
|---------|-------------------|----------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|\-6|  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [邏輯 NOT 運算子 \(\!\)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)