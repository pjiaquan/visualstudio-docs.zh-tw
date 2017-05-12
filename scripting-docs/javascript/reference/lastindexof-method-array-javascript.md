---
title: "lastIndexOf 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "陣列 [JavaScript], lastIndexOf 方法"
  - "lastIndexOf 方法 [JavaScript]"
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# lastIndexOf 方法 (Array) (JavaScript)
傳回陣列中最後一個符合指定值的元素索引。  
  
## 語法  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`array1`|必要項。  要搜尋的陣列物件。|  
|`searchElement`|必要項。  要在 `array1` 中尋找的值。|  
|`fromIndex`|選擇項。  開始搜尋時的陣列索引。  如果省略 `fromIndex`，就會從陣列的最後一個索引位置開始搜尋。|  
  
## 傳回值  
 陣列中最後一次出現 `searchElement` 的索引位置，如果找不到 `searchElement` 則為 \-1。  
  
## 備註  
 `lastIndexOf` 方法會在陣列中搜尋指定的值，  並傳回第一個相符的元素，如果找不到指定值則傳回 \-1。  
  
 搜尋時，會依遞減的索引順序進行 \(即從最後一個成員開始\)。  若要依遞增順序搜尋，請使用 [indexOf 方法 \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)。  
  
 比對陣列元素時，是將元素與 `searchElement` 值進行嚴格相等比較，這就類似使用 `===` 運算子進行比較。  如需詳細資訊，請參閱[比較運算子](../../javascript/reference/comparison-operators-javascript.md)。  
  
 選擇性的 `fromIndex` 引數會指定開始搜尋時的陣列索引。  如果 `fromIndex` 大於或等於陣列長度，則會搜尋整個陣列。  如果 `fromIndex` 是負值，那麼索引位置就是陣列長度加上 `fromIndex` 的總和，並從該位置開始搜尋。  如果總和小於 0，則會傳回 \-1。  
  
## 範例  
 在下列範例中，說明了如何使用 `lastIndexOf` 方法。  
  
```javascript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [indexOf 方法 \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)