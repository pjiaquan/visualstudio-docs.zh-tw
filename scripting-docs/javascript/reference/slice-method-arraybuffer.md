---
title: "slice 方法 (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# slice 方法 (ArrayBuffer)
傳回 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 的一個區段。  
  
## 語法  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## 參數  
 `arrayBufferObj`  
 必要項。  從中複製區段的 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 物件。  
  
 `start`  
 必要項。  要複製之區段開頭的位元組索引。  
  
 `end`  
 選擇項。  要複製之區段結尾的位元組索引。  
  
## 備註  
 `slice` 方法傳回 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 物件，內含 `arrayBufferObj` 的指定部分。  
  
 `slice` 方法會複製到 \(但不含\) `end` 所指出的位元組。  如果 `start` 或 `end` 是負值，則會分別將指定的索引視為 `length` \+ `start` 或 `end`，其中 `length` 是 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 的長度。  如果省略 `end`，則會一直擷取到 `arrayBufferObj` 的結尾。  如果 `end` 位在 `start` 的前面，則不會將位元組複製至新的 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。  
  
## 範例  
 下列範例顯示如何使用 `slice` 方法。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## 需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 請參閱  
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)