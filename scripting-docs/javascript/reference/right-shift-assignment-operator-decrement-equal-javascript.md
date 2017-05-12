---
title: "右移指派運算子 (&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>= 運算子 [JavaScript]"
  - "指派運算子, JavaScript"
  - "向右移位運算子 [JavaScript]"
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 右移指派運算子 (&gt;&gt;=) (JavaScript)
利用運算式值中所指定的位元數來將變數值向右移位，保持正負號不變，然後將結果指派給變數。  
  
## 語法  
  
```  
  
result >>= expression  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression*  
 任何運算式。  
  
## 備註  
 使用 **\>\>\=** 運算子與以下的指定方式完全相同：  
  
```javascript  
result = result >> expression  
```  
  
 **\>\>\=** 運算子會將 *result* 的位元向右移位 *expression* 中所指定的位元數。  *result* 的正負號位元是用來填滿左邊的數字。  移出右邊界的數字會被捨棄。  例如，在評估以下程式碼之後，*temp* 的值為 \-4：14 \(二進位為 11110010\) 向右移兩位元就等於 \-4 \(二進位為 11111100\)。  
  
```javascript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元左移運算子 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [位元右移運算子 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [不帶正負號的右移運算子 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)