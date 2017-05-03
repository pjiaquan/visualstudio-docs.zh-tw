---
title: "位元 AND 運算子 (&amp;) (JavaScript) | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "指派運算子，位元 [JavaScript]"
  - "& 運算子，關於 & 運算子"
  - "AND 運算子"
  - "& 運算子"
  - "位元運算子，AND 運算子"
  - "& 運算子，位元運算子"
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 位元 AND 運算子 (&amp;) (JavaScript)
針對兩個 32 位元運算式執行位元 AND 運算。  
  
## 語法  
  
```  
  
result = expression1 & expression2  
```  
  
## 參數  
 `result`  
 運算的結果。  
  
 `expression1`  
 任何運算式。  
  
 `expression2`  
 任何運算式。  
  
## 備註  
 `&` 會針對兩個 32 位元運算式的每個位元執行位元 AND 運算。  如果兩個位元都是 1，則結果為 1。  否則，產生結果是 0。  
  
|位元 1|位元 2|ANDed 值|  
|----------|----------|-------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 下列範例示範如何使用 `&` 運算子。  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元 AND 指派運算子 \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)