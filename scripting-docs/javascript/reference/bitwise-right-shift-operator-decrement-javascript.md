---
title: "位元右移運算子 (&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">> 運算子"
  - ">> 運算子, 關於 >> 運算子"
  - ">> 運算子, 位元集"
  - "位元運算子, 右移運算子"
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 位元右移運算子 (&gt;&gt;) (JavaScript)
將運算式的位元向右移位，正負號保持不變。  
  
## 語法  
  
```  
  
result = expression1 >> expression2  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## 備註  
 \>\> 運算子會將 *expression1* 的位元向右移 *expression2* 中指定的位元數。  *expression1* 的正負號位元是用來從左邊開始填滿數字。  移出右邊界的數字會被捨棄。  例如，在評估過下列程式碼之後，*temp* 具有 \-4 的值：\-14 \(二進位數字之二的補數中的 11110010\) 向右移兩個位元就等於 \-4 \(二進位數字之二的補數中的 11111100\)。  
  
```javascript  
var temp  
temp = -14 >> 2  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元左移運算子 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [右移設定運算子 \(\>\>\=\)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [不帶正負號的右移運算子 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)