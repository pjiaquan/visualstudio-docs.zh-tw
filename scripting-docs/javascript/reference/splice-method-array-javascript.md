---
title: "splice 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "splice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "splice 方法"
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# splice 方法 (陣列) (JavaScript)
移除陣列中的元素，並依需要在這些位置插入新元素，然後傳回被刪除的元素。  
  
## 語法  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## 參數  
 `arrayObj`  
 必要項。  `Array` 物件。  
  
 `start`  
 必要項。  陣列中要開始移除元素的位置 \(以零為起始\)。  
  
 `deleteCount`  
 必要項。  要移除的元素數目。  
  
 `item1, item2,. . ., itemN`  
 選擇項。  要插入陣列中的元素，以取代被刪除的元素。  
  
## 備註  
 `splice` 方法修改 `arrayObj` 的方式是從 `start` 位置開始移除指定的元素個數，然後插入新元素。  刪除的元素會當做新的 `Array` 物件傳回。  
  
## 範例  
 下列程式碼將示範如何使用 `splice` 方法。  
  
```javascript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [slice 方法 \(陣列\)](../../javascript/reference/slice-method-array-javascript.md)