---
title: "subarray 方法 (Float32Array) | Microsoft Docs"
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
ms.assetid: 97aa27c0-d650-411e-b929-dd9c4a2ae9a5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray 方法 (Float32Array)
指定子陣列的第一個和最後一個成員，為這個陣列取得 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md) 存放區的新 Float32Array 檢視。  
  
## 語法  
  
```javascript  
var newFloat32Array = float32Array.subarray(begin, end);  
```  
  
## 參數  
 `newFloat32Array`  
 這個方法所傳回的子陣列。  
  
 `begin`  
 陣列開頭的索引。  
  
 `end`  
 陣列結尾的索引。  
  
## 備註  
 如果 `begin` 或 `end` 是負值，就表示索引要從陣列結尾起算，而非從開頭起算。  如果未指定 `end`，子陣列就包含從型別陣列的 `begin` 到結尾的所有元素。  `begin` 和 `end` 值所指定的範圍僅限於目前陣列的有效索引範圍。  如果新的型別陣列，其長度經計算後為負值，則會設定為零。  傳回的陣列與叫用此方法的來源陣列都是相同型別。  
  
## 範例  
 下列範例示範如何從來源陣列的第一個元素開始，取得包含三個元素的子陣列。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]