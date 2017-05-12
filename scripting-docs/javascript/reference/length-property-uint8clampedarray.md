---
title: "length 屬性 (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: de8065a7-04a5-43fa-b5d8-fb2f6c065bfc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# length 屬性 (Uint8ClampedArray)
陣列的長度。  
  
## 語法  
  
```javascript  
var arrayLength = uint8ClampedArray.length;  
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
            alert(intArr.length);  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 請參閱  
 [Uint8ClampedArray 物件](../../javascript/reference/uint8clampedarray-object-javascript.md)