---
title: "位元 XOR 指派運算子 (^=) (JavaScript) | Microsoft Docs"
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
  - "^="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "^= 運算子"
  - "^= 運算子, 關於 ^= 運算子"
  - "指派運算子, 位元 [JavaScript]"
  - "位元運算子, XOR 運算子"
  - "XOR 運算子"
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 位元 XOR 指派運算子 (^=) (JavaScript)
針對變數和運算式執行位元互斥 OR 運算，然後將結果指派給變數。  
  
## 語法  
  
```  
  
result ^= expression  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression*  
 任何運算式。  
  
## 備註  
 使用 **^\=** 運算子與以下的指定方式完全相同：  
  
```javascript  
result = result ^ expression  
```  
  
 **^\=** 運算子會檢查以二進位表示的兩個運算式值，並針對兩個運算式執行位元互斥 OR 運算。  運算結果如下：  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 如果其中一個運算式值有一個位數是 1，結果值中的該位數就是 1。  否則，結果值中的該位數為 0。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元 XOR 運算子 \(^\)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)