---
title: "不帶正負號的右移指派運算子 (&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>>= 運算子"
  - "指派運算子, JavaScript"
  - "不帶正負號的右移指派運算子 (>>>=)"
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 不帶正負號的右移指派運算子 (&gt;&gt;&gt;=) (JavaScript)
將變數值向右移位運算式值中所指定的位元數 \(不保留正負號\)，然後將結果指派給變數。  
  
## 語法  
  
```  
  
result >>>= expression  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression*  
 任何運算式。  
  
## 備註  
 使用 \>\>\>\= 運算子與以下的操作方式完全相同：  
  
```javascript  
result = result >>> expression  
```  
  
 **\>\>\>\=** 運算子會將 *result* 的位元向右移位 *expression* 中所指定的位元數。  從左邊開始填入零。  移出右邊界的數字會被捨棄。  例如：  
  
```javascript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 變數 *temp* 的初始值是 \-14 \(二進位數字之二的補數中的 11111111 11111111 11111111 11110010\)。  向右移兩個位元時，值就等於 1073741820 \(二進位為 00111111 11111111 11111111 11111100\)。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [不帶正負號的右移運算子 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [位元左移運算子 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [位元右移運算子 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)