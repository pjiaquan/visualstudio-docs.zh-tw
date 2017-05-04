---
title: "DataView 物件 | Microsoft Docs"
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DataView 物件
您可以使用 DataView 物件，在 ArrayBuffer 中的任何位置讀取和寫入各種不同的二進位資料。  
  
## 語法  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## 參數  
 `dataView`  
 必要項。  指派 **DataView** 物件的變數名稱。  
  
 `buffer`  
 DataView 表示的 ArrayBuffer。  
  
 `byteOffset`  
 選擇項。  指定從緩衝區開頭 \(也就是 DataView 應該開始的地方\) 算起的位移 \(以位元組為單位\)。  
  
 `byteLength`  
 選擇項。  指定 DataView 所代表的緩衝區區段長度 \(以位元組為單位\)。  
  
## 備註  
 如果同時省略 byteOffset 和 byteLength，則 DataView 擴及整個 ArrayBuffer 範圍。  如果省略 byteLength，DataView 的範圍會從指定的 byteOffset 延伸到 ArrayBuffer 的結尾。  如果指定的 byteOffset 和 byteLength 參考到超出 ArrayBuffer 結尾的區域，就會引發例外狀況。  
  
## 屬性  
 下表列出 `DataView` 物件的屬性。  
  
|屬性|描述|  
|--------|--------|  
|[buffer 屬性](../../javascript/reference/buffer-property-dataview.md)|唯讀。  取得這個檢視所參考的 ArrayBuffer。|  
|[byteLength 屬性](../../javascript/reference/bytelength-property-dataview.md)|唯讀。  這個檢視從其 ArrayBuffer 開頭算起的長度 \(以位元組為單位\)，在建構階段長度都不會改變。|  
|[byteOffset 屬性](../../javascript/reference/byteoffset-property-dataview.md)|唯讀。  這個檢視從其 ArrayBuffer 開頭算起的位移 \(以位元組為單位\)，在建構階段位移都不會改變。|  
  
## 方法  
 下表列出 `DataView` 物件的方法。  
  
|方法|描述|  
|--------|--------|  
|[getInt8 方法](../../javascript/reference/getint8-method-dataview.md)|在由檢視開頭起算指定之位元組位移處取得 Int8 值。|  
|[getUint8 方法 \(DataView\)](../../javascript/reference/getuint8-method-dataview.md)|在由檢視開頭起算指定之位元組位移處取得 Uint8 值。|  
|[getInt16 方法 \(DataView\)](../../javascript/reference/getint16-method-dataview.md)|在由檢視開頭起算指定之位元組位移處取得 Int16 值。|  
|[getUint16 方法 \(DataView\)](../../javascript/reference/getuint16-method-dataview.md)|在由檢視開頭起算指定之位元組位移處取得 Uint16 值。|  
|[getInt32 方法 \(DataView\)](../../javascript/reference/getint32-method-dataview.md)|在由檢視開頭起算指定之位元組位移處取得 Int32 值。|  
|[getUint32 方法 \(DataView\)](../../javascript/reference/getuint32-method-dataview.md)|在由檢視開頭起算指定之位元組位移處取得 Uint32 值。|  
|[getFloat32 方法 \(DataView\)](../../javascript/reference/getfloat32-method-dataview.md)|在由檢視開頭起算指定之位元組位移處取得 Float32 值。|  
|[getFloat64 方法 \(DataView\)](../../javascript/reference/getfloat64-method-dataview.md)|在由檢視開頭起算指定之位元組位移處取得 Float64 值。|  
|[setInt8 方法 \(DataView\)](../../javascript/reference/setint8-method-dataview.md)|在從檢視開頭算起的指定位元組位移處儲存 Int8 值。|  
|[setUint8 方法 \(DataView\)](../../javascript/reference/setuint8-method-dataview.md)|在從檢視開頭算起的指定位元組位移處儲存 Uint8 值。|  
|[setInt16 方法 \(DataView\)](../../javascript/reference/setint16-method-dataview.md)|在從檢視開頭算起的指定位元組位移處儲存 Int16 值。|  
|[setUint16 方法 \(DataView\)](../../javascript/reference/setuint16-method-dataview.md)|在從檢視開頭算起的指定位元組位移處儲存 Uint16 值。|  
|[setInt32 方法 \(DataView\)](../../javascript/reference/setint32-method-dataview.md)|在從檢視開頭算起的指定位元組位移處儲存 Int32 值。|  
|[setUint32 方法 \(DataView\)](../../javascript/reference/setuint32-method-dataview.md)|在從檢視開頭算起的指定位元組位移處儲存 Uint32 值。|  
|[setFloat32 方法 \(DataView\)](../../javascript/reference/setfloat32-method-dataview.md)|在從檢視開頭算起的指定位元組位移處儲存 Float32 值。|  
|[setFloat64 方法 \(DataView\)](../../javascript/reference/setfloat64-method-dataview.md)|在從檢視開頭算起的指定位元組位移處儲存 Float64 值。|  
  
## 範例  
 下列範例示範如何使用 DataView 物件來處理從 XmlHttpRequest 取得的二進位資料：  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]