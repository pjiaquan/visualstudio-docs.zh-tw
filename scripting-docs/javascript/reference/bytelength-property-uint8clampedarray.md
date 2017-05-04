---
title: "byteLength 屬性 (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 37ae1728-8e2c-496c-bb77-f5f85b1ecbba
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# byteLength 屬性 (Uint8ClampedArray)
唯讀。  這個陣列從其 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 開頭算起的長度 \(以位元組為單位\)，在建構階段長度都不會改變。  
  
## 語法  
  
```javascript  
var arrayByteLength = uint8ClampedArray.byteLength;  
```  
  
## 範例  
 下列範例將示範如何取得陣列的長度。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.byteLength);  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 請參閱  
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray 物件](../../javascript/reference/uint8clampedarray-object-javascript.md)