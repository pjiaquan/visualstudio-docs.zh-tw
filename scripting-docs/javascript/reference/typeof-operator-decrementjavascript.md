---
title: "typeof 運算子 (JavaScript) | Microsoft Docs"
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
  - "typeof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "typeof 運算子"
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# typeof 運算子 (JavaScript)
傳回可識別運算式之資料類型的字串。  
  
## 語法  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## 備註  
 *expression* 引數是要尋找其類型資訊的任何運算式。  
  
 `typeof` 運算子會以字串傳回類型資訊。  `typeof` 可能會傳回的六個值如下："number"、"string"、"boolean"、"object"、"function" 和 "undefined"。  
  
 在 `typeof` 語法中的括號是選擇性的。  
  
## 範例  
 下列範例會測試變數的資料類型。  
  
```javascript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## 範例  
 下列範例會測試 `undefined` 的資料類型，以找出宣告和未宣告的變數。  
  
```javascript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [Array.isArray 函式](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf 函式](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined 常數](../../javascript/reference/undefined-constant-javascript.md)   
 [比較運算子](../../javascript/reference/comparison-operators-javascript.md)   
 [資料類型](../../javascript/data-types-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)