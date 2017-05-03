---
title: "Array.isArray 函式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array.isArray 函式 [JavaScript]"
  - "isArray 函式 [JavaScript]"
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Array.isArray 函式 (JavaScript)
判斷某個物件是否為陣列。  
  
## 語法  
  
```  
Array.isArray(object)   
```  
  
#### 參數  
 `object`  
 必要項。  要測試的物件。  
  
## 傳回值  
 如果 `object` 是陣列，則為 `true`，否則為 `false`。  如果 `object` 引數不是物件， 會傳回 `false`。  
  
## 範例  
 下面範例說明 `Array.isArray` 函式的使用。  
  
```javascript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof 運算子](../../javascript/reference/typeof-operator-decrementjavascript.md)