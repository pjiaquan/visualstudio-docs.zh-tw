---
title: "slice 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "以零為起始的索引"
  - "Array 物件"
  - "slice 方法"
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# slice 方法 (Array) (JavaScript)
傳回陣列的其中一部分。  
  
## 語法  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## 參數  
 `arrayObj`  
 必要項。  `Array` 物件。  
  
 `start`  
 必要項。  `arrayObj` 之指定部分的開頭。  
  
 `end`  
 選擇項。  `arrayObj` 之指定部分的結尾。  
  
## 備註  
 `slice` 方法會傳回 `Array` 物件，其中包含 `arrayObj` 的指定部分。  
  
 `slice` 方法會複製元素一直到 `end` 所代表的元素，但並不包括此元素。  如果 `start` 是負值，則這個值會被視為是 `length` \+ `start`，其中 `length` 是這個陣列的長度。  如果 `end` 是負值，則這個值會被視為是 `length` \+ `end`，其中 `length` 是這個陣列的長度。  如果省略 `end`，就會繼續擷取，一直到 `arrayObj` 的結尾。  如果 `end` 出現在 `start` 之前，則不會複製任何元素到新陣列之中。  
  
## 範例  
 下列範例示範如何使用 `slice` 方法。  第一個範例會將 `myArray` 最後一個以外的所有元素都複製到 `newArray` 中，  而第二個範例只會將 `myArray` 的最後兩個元素複製到 `newArray`。  
  
```javascript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [slice 方法 \(字串\)](../../javascript/reference/slice-method-string-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)