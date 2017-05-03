---
title: "getFloat32 方法 (DataView) | Microsoft Docs"
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
ms.assetid: adecf671-bde4-46be-a875-33b6d6e970b1
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# getFloat32 方法 (DataView)
在從檢視開頭算起的指定位元組位移處取得 Float32 值。  由於沒有對齊條件約束，所以可以從任何位移擷取多位元組值。  
  
## 語法  
  
```  
var testFloat = dataView.getFloat32(byteOffset, littleEndian);   
```  
  
## 參數  
 `testFloat`  
 必要項。  從此方法傳回的 Float32 值。  
  
 `byteOffset`  
 應該在緩衝區中擷取之值的位置。  
  
 `littleEndian`  
 選擇項。  如果是 false 或 undefined，就會讀取位元組由大到小的值，否則會讀取位元組由小到大的值。  
  
## 備註  
 如果這些方法讀取的範圍超出檢視的結尾，就會引發例外狀況。  
  
## 範例  
 下列範例示範如何在 DataView 中取得第一個 Float32。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat32(0));  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]