---
title: "forEach 方法 (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# forEach 方法 (Set) (JavaScript)
針對集合的每一個項目執行指定之動作。  
  
## 語法  
  
```javascript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### 參數  
 `setObj`  
 必要項。  `Set` 物件。  
  
 `callbackfn`  
 必要項。  `callbackfn` 最多接受三個引數。  `forEach` 針對集合中每個項目各呼叫一次的函式。  
  
 `thisArg`  
 選擇項。  `this` 關鍵字可在 `callbackfn` 函式中參考的物件。  如果省略 `thisArg`，則 `this` 值就是 `undefined`。  
  
## 例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## 備註  
 回呼函式的語法如下：  
  
 `function callbackfn(value, key, setObj)`  
  
 您最多可以使用三個參數宣告回呼函式，如下表所示。  
  
|回呼引數|定義|  
|----------|--------|  
|`value`|集合中包含的值。|  
|`key`|集合中包含的值。  集合沒有任何索引鍵，因此這個值與 `value` 相同。|  
|`setObj`|要周遊的 `Set` 物件。|  
  
## 範例  
 下列範例顯示如何使用 `forEach`。  `callbackfn` 引數包含回呼函式的程式碼。  
  
```javascript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## 範例  
 下列範例顯示，只傳遞一個參數至回呼函式，也可以從集合中擷取成員。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]