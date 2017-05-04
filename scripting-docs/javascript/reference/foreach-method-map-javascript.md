---
title: "forEach 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# forEach 方法 (Map) (JavaScript)
針對對應的每一個項目執行指定之動作。  
  
## 語法  
  
```javascript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### 參數  
 `mapObj`  
 必要項。  `Map` 物件。  
  
 `callbackfn`  
 必要項。  `forEach` 針對對應中每個項目各呼叫一次的函式。  `callbackfn` 最多接受三個引數。  `forEach` 會針對地圖中的每個項目各呼叫 `callbackfn` 函式一次。  
  
 `thisArg`  
 選擇項。  `this` 關鍵字可在 `callbackfn` 函式中參考的物件。  如果省略 `thisArg`，則 `this` 值就是 `undefined`。  
  
## 例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## 備註  
 回呼函式的語法如下：  
  
 `function callbackfn(value, key, mapObj)`  
  
 您最多可以使用三個參數宣告回呼函式，如下表所示。  
  
|回呼引數|定義|  
|----------|--------|  
|`value`|對應中包含的值。|  
|`key`|對應中包含的索引鍵。|  
|`mapObj`|要周遊的 `Map` 物件。|  
  
## 範例  
 下列範例示範如何使用 `forEach` 擷取 `Map` 的成員。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]