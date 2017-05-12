---
title: "不帶正負號的右移運算子 (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>> 運算子"
  - "不帶正負號的右移運算子 (>>>)"
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 不帶正負號的右移運算子 (&gt;&gt;&gt;) (JavaScript)
將運算式的位元向右移位，不需保留正負號。  
  
## 語法  
  
```  
  
result = expression1 >>> expression2  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## 備註  
 **\>\>\>** 運算子會將 *expression1* 的位元向右移 *expression2* 中指定的位元數。  從左邊開始填入零。  移出右邊界的數字會被捨棄。  例如：  
  
```javascript  
var temp  
temp = -14 >>> 2  
```  
  
 變數 *temp* 的初始值是 \-14 \(二進位數字之二的補數中的 11111111 11111111 11111111 11110010\)。  向右移兩個位元時，值就等於 1073741820 \(二進位為 00111111 11111111 11111111 11111100\)。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [不帶正負號的右移設定運算子 \(\>\>\>\=\)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [位元左移運算子 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [位元右移運算子 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)