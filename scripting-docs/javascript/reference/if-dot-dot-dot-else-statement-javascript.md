---
title: "if...else 陳述式 (JavaScript) | Microsoft Docs"
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
  - "else_JavaScriptKeyword"
  - "if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "if 陳述式, if...else"
  - "迴圈結構, if...else 陳述式"
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# if...else 陳述式 (JavaScript)
根據運算式的值，有條件地執行一組陳述式。  
  
## 語法  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## 參數  
 `condition1`  
 必要項。  Boolean 運算式。  如果 `condition1` 是 `null` 或 `undefined`，`condition1` 會被視為 `false`。  
  
 `statement1`  
 選擇項。  當 `condition1` 為 **true** 時要執行的陳述式。  可以是複合陳述式。  
  
 `condition2`  
 要評估的條件。  
  
 `statement2`  
 選擇項。  當 `condition2` 為 `true` 時要執行的陳述式。  可以是複合陳述式。  
  
 `statement3`  
 如果 `condition1` 和 `condition2` 都是 `false`，便會執行這個陳述式。  
  
## 範例  
 下列程式碼會示範如何使用 `if`、`if else` 和 `else`。  
  
 最好將 `statement1` 和 `statement2` 放在大括號 \({}\) 裡面，如此較能清楚表達，並避免不小心的錯誤。  
  
```javascript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [條件 \(三元\) 運算子 \(?:\)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)