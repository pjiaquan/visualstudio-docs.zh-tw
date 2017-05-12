---
title: "Array.of 函式 (陣列) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.of 函式 (陣列) (JavaScript)
從傳入的引數傳回陣列。  
  
## 語法  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### 參數  
 `element0,...,elementN`  
 選擇項。  要放置在陣列中的項目。  這樣會建立有 n \+ 1 個項目的陣列，而且長度為 n \+ 1。  
  
## 備註  
 此函式類似於呼叫 `new Array(args)`，但傳入一個引數時，`Array.of` 不包含特殊行為。  
  
## 範例  
 下列範例會從傳入的數字建立陣列。  
  
```javascript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1  
  
```  
  
## 範例  
 下例顯示使用 `Array.of` 和 `new Array` 的差異。  
  
```javascript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]