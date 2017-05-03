---
title: "push 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "push"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Push 方法"
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# push 方法 (陣列) (JavaScript)
附加新元素到陣列中，並傳回陣列的新長度。  
  
## 語法  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## 參數  
 `arrayObj`  
 必要項。  `Array` 物件。  
  
 `item, item2,. . ., itemN`  
 選擇項。  `Array` 的新元素。  
  
## 備註  
 `push` 和 `pop` 方法可讓您模擬後進先出的堆疊。  
  
 `push` 方法會將元素依出現的順序附加上去。  如果其中一個引數是陣列，則會將它當成單一元素加入。  若要聯結兩個以上陣列的元素，可使用 `concat` 方法。  
  
## 範例  
 在下列範例中，說明了如何使用 `push` 方法。  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [concat 方法 \(陣列\)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop 方法 \(陣列\)](../../javascript/reference/pop-method-array-javascript.md)