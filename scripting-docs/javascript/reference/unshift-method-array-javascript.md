---
title: "unshift 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "unshift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unshift 方法"
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# unshift 方法 (陣列) (JavaScript)
在陣列的開頭插入新元素。  
  
## 語法  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## 參數  
 `arrayObj`  
 必要項。  `Array` 物件。  
  
 `item1, item2,. . ., itemN`  
 選擇項。  要插在 `Array` 開頭的元素。  
  
## 備註  
 `unshift` 方法會將元素插入陣列的開頭，使它們能夠依照引數清單中的順序出現。  
  
## 範例  
 在下列範例中，說明了如何使用 `unshift` 方法。  
  
```javascript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [shift 方法 \(陣列\)](../../javascript/reference/shift-method-array-javascript.md)