---
title: "pop 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "pop"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Pop 方法"
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# pop 方法 (陣列) (JavaScript)
移除陣列的最後一個元素，然後將它傳回。  
  
## 語法  
  
```  
  
arrayObj.pop( )  
```  
  
## 備註  
 [push](../../javascript/reference/push-method-array-javascript.md) 和 `pop` 方法可讓您模擬堆疊，以使用後進先出 \(LIFO\) 的原則儲存資料。  
  
 必要的 `arrayObj` 參考是 `Array` 物件。  
  
 如果是空陣列，則會傳回 `undefined`。  
  
## 範例  
 在下列範例中，說明了如何使用 `pop` 方法。  
  
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
  
// Output: 9 8 7 6 5  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [push 方法 \(陣列\)](../../javascript/reference/push-method-array-javascript.md)