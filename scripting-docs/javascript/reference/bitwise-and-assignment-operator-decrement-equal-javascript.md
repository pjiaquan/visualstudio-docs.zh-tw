---
title: "位元 AND 指派運算子 (&amp;=) (JavaScript) | Microsoft Docs"
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
  - "&="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&= 運算子"
  - "指派運算子，位元 [JavaScript]"
  - "AND 運算子"
  - "位元運算子，AND 運算子"
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 位元 AND 指派運算子 (&amp;=) (JavaScript)
設定變數值和運算式值的位元 AND 運算的結果。  變數和運算式會被視為是 32 位元整數。  
  
## 語法  
  
```  
  
result &= expression  
```  
  
## 參數  
 `result`  
 任何變數。  
  
 `expression`  
 任何運算式。  
  
## 備註  
 使用這個運算子等同於指定：  
  
```javascript  
result = result & expression  
```  
  
 [位元 AND 運算子 \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) 會查看以二進位表示的 `result` 及 `expression` 的值，然後針對這兩個值執行位元 AND 運算。  這項作業的輸出行為如下：  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
  
```  
  
 如果兩個運算式的數字中都有 1，結果的數字才會有 1。  否則，結果值中的該位數為 0。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元 AND 運算子 \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)