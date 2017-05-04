---
title: "indexOf 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "陣列 [JavaScript], indexOf 方法"
  - "indexOf 方法 [JavaScript]"
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# indexOf 方法 (Array) (JavaScript)
傳回陣列中第一個與值相符的元素索引。  
  
## 語法  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`array1`|必要項。  陣列物件。|  
|`searchElement`|必要項。  要在 `array1` 中尋找的值。|  
|`fromIndex`|選擇項。  開始搜尋時的陣列索引。  如果省略 `fromIndex`，就會從索引 0 的位置開始搜尋。|  
  
## 傳回值  
 陣列中第一次出現 `searchElement` 的索引位置，如果找不到 `searchElement` 則為 \-1。  
  
## 備註  
 `indexOf` 方法會在陣列中搜尋指定的值。  並傳回第一個相符的元素，如果找不到指定值則傳回 \-1。  
  
 搜尋會以索引遞增順序進行。  
  
 陣列元素會與 `searchElement` 值進行嚴格等號比較，類似於 `===` 運算子。  如需詳細資訊，請參閱[比較運算子](../../javascript/reference/comparison-operators-javascript.md)。  
  
 選擇性的 `fromIndex` 引數會指定開始搜尋時的陣列索引。  如果 `fromIndex` 大於或等於陣列長度，則會傳回 \-1。  如果 `fromIndex` 是負值，那麼索引位置就是陣列長度加上 `fromIndex` 的總和，並從該位置開始搜尋。  
  
## 範例  
 在下列範例中，說明了如何使用 `indexOf` 方法。  
  
```javascript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)