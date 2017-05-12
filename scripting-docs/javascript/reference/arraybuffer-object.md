---
title: "ArrayBuffer 物件 | Microsoft Docs"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ArrayBuffer 物件
代表二進位資料的原始緩衝區，用來儲存不同類型陣列的資料。  無法直接讀取或寫入 `ArrayBuffers`，但是可以傳遞給類型陣列或 [DataView 物件](../../javascript/reference/dataview-object.md)，以視需要解譯原始緩衝區。  
  
 如需類型陣列的詳細資訊，請參閱 [具類型陣列](../../javascript/advanced/typed-arrays-javascript.md)。  
  
## 語法  
  
```javascript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## 參數  
 `arrayBuffer`  
 必要項。  要對其指派 `ArrayBuffer` 物件的變數名稱。  
  
 `length`  
 緩衝區的長度。  ArrayBuffer 的內容已初始化為 0。  如果無法配置要求的位元組數目，就會引發例外狀況。  
  
## 屬性  
 下表列出 `ArrayBuffer` 物件的屬性。  
  
|屬性|描述|  
|--------|--------|  
|[byteLength 屬性](../../javascript/reference/bytelength-property-arraybuffer.md)|唯讀。  ArrayBuffer 的長度 \(以位元組為單位\)。|  
  
## 函式  
 下表列出 `ArrayBuffer` 物件的函式。  
  
|屬性|描述|  
|--------|--------|  
|[ArrayBuffer.isView 函式](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|決定物件是否提供緩衝區的檢視。|  
  
## 方法  
 下表列出 `ArrayBuffer` 物件的方法。  
  
|屬性|描述|  
|--------|--------|  
|[slice 方法](../../javascript/reference/slice-method-arraybuffer.md)|傳回 `ArrayBuffer` 的一個區段。|  
  
## 範例  
 下列範例顯示如何使用 ArrayBuffer 物件來處理取自 [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx) \(英文\) 的二進位資料。  您可以使用 [DataView 物件](../../javascript/reference/dataview-object.md) 取得個別值。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 備註  
 如需有關使用 `XmlHttpRequest` 的詳細資訊，請參閱[XMLHttpRequest enhancements](http://msdn.microsoft.com/zh-tw/be09137c-6546-441b-b953-dcbf72b77069)。  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]