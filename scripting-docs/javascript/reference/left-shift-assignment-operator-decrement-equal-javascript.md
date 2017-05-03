---
title: "左移指派運算子 (&lt;&lt;=) (JavaScript) | Microsoft Docs"
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
  - "<<="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<<= 運算子 [JavaScript]"
  - "左移指派運算子 (<<=) [JavaScript]"
  - "向左移位運算子 [JavaScript]"
  - "指派運算子，JavaScript"
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 左移指派運算子 (&lt;&lt;=) (JavaScript)
向左移動指定的位元數，並將結果指派給 `result`。  此作業所空出的位元會填滿 0。  
  
## 語法  
  
```  
  
result <<= expression  
```  
  
## 參數  
 `result`  
 任何變數。  
  
 `expression`  
 要移動的位元數。  
  
## 備註  
 使用 `<<=` 運算子與指定 `result = result << expression` 相同  
  
 下列範例示範如何使用 `<<=` 運算子。  
  
```javascript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元左移運算子 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [位元右移運算子 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [不帶正負號的右移運算子 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)