---
title: "set 方法 (Float64Array) | Microsoft Docs"
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
ms.assetid: 694965e6-503d-4aaa-8340-63455e96ddf6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# set 方法 (Float64Array)
設定一個值或值陣列。  
  
## 語法  
  
```javascript  
float64Array.set(index, value);  
float64Array.set(array, offset);  
  
```  
  
## 參數  
 `index`  
 要設定之位置的索引。  
  
 `value`  
 要設定的值。  
  
 `array`  
 要設定之具類型或不具類型的值陣列。  
  
 `offset`  
 目前陣列中的索引，這些值將會寫入至這個位置。  
  
## 備註  
 如果輸入陣列是 TypedArray，則這兩個陣列可以使用相同的基礎 ArrayBuffer。  在這種情況下設定值時，就如同先將所有資料都複製到不與其中任何一個陣列重疊的暫存緩衝區，再將資料從暫存緩衝區複製到目前的陣列一般。  
  
 如果 offset 與指定的陣列長度總和超出目前 TypedArray 的範圍，就會引發例外狀況。  
  
## 範例  
 下列範例將示範如何設定陣列的第一個元素。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            floatArr.set(0, 9.1);  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]