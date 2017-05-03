---
title: "位元左移運算子 (&lt;&lt;) (JavaScript) | Microsoft Docs"
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
  - "<<"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<< 運算子"
  - "<< 運算子, 關於 << 運算子"
  - "位元運算子, 左移運算子"
  - "左移運算子"
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 位元左移運算子 (&lt;&lt;) (JavaScript)
將運算式的位元向左移位。  
  
## 語法  
  
```  
  
result = expression1 << expression2  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## 備註  
 **\<\<** 運算子會將 *expression1* 的位元向左移 *expression2* 中指定的位元數。  例如：  
  
```javascript  
var temp  
temp = 14 << 2  
```  
  
 變數 *temp* 的值為 56，因為 14 \(二進位為 00001110\) 向左移兩位元就等於 56 \(二進位為 00111000\)。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [左移設定運算子 \(\<\<\=\)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [位元右移運算子 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [不帶正負號的右移運算子 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)