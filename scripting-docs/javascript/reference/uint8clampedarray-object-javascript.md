---
title: "Uint8ClampedArray 物件 (JavaScript) | Microsoft Docs"
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Uint8ClampedArray 物件 (JavaScript)
8 位元不帶正負號整數 \(值壓制為範圍 0\-255\) 的類型陣列。  內容已初始化為 0。  如果無法配置要求的位元組數目，就會擲回例外狀況。  
  
## 語法  
  
```  
  
uint8ClampedArray = new Uint8ClampedArray( length ); uint8ClampedArray = new Uint8ClampedArray( array ); uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## 參數  
 `uint8ClampedArray`  
 必要項。  要對其指派 `Uint8ClampedArray` 物件的變數名稱。  
  
 `length`  
 選擇項。  陣列中的元素數目。  
  
 `array`  
 選擇項。  這個陣列中所包含的陣列 \(或類型陣列\)。  內容會初始化為所指定陣列或類型陣列的內容，其中每個項目都會轉換成 `Uint8` 類型。  
  
 `buffer`  
 選擇項。  `Uint8ClampedArray` 所代表的 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。  
  
 `byteOffset`  
 選擇項。  從緩衝區開頭 \(也就是 `Uint8ClampedArray` 應該開始的位置\) 算起的位移 \(以位元組為單位\)。  
  
 `length`  
 選擇項。  陣列中的元素數目。  
  
## 備註  
 `Uint8ClampedArray` 物件中所儲存的值介於 0 與 255 之間。  如果您將陣列成員設為負值，則會將值設為 0。  如果您設定的值大於 255，則會將值設為 255。  
  
 `Uint8ClampedArray` 物件中的值會四捨五入為最接近的事件值，稱為「四捨六入五成雙」。  
  
## 常數  
 下表列出 `Uint8ClampedArray` 物件的常數。  
  
|常數|描述|  
|--------|--------|  
|[BYTES\_PER\_ELEMENT 常數](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|陣列中每個項目的大小 \(以位元組為單位\)。|  
  
## 屬性  
 下表列出 `Uint8ClampedArray` 物件的常數。  
  
|屬性|描述|  
|--------|--------|  
|[buffer 屬性](../../javascript/reference/buffer-property-uint8clampedarray.md)|唯讀。  取得這個陣列所參考的 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。|  
|[byteLength 屬性](../../javascript/reference/bytelength-property-uint8clampedarray.md)|唯讀。  這個陣列從其 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 開頭算起的長度 \(以位元組為單位\)，在建構階段長度都不會改變。|  
|[byteOffset 屬性](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|唯讀。  這個陣列從其 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 開頭算起的位移 \(以位元組為單位\)，在建構階段長度都不會改變。|  
|[length 屬性](../../javascript/reference/length-property-uint8clampedarray.md)|陣列的長度。|  
  
## 方法  
 下表列出 `Uint8ClampedArray` 物件的方法。  
  
|方法|描述|  
|--------|--------|  
|[set 方法](../../javascript/reference/set-method-uint8clampedarray.md)|設定一個值或值陣列。|  
|[subarray 方法](../../javascript/reference/subarray-method-uint8clampedarray.md)|指定子陣列的第一個和最後一個項目，為這個陣列取得 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 存放區的新 `Uint8ClampedArray` 檢視。|  
  
## 範例  
 下列範例將示範如何使用 `Uint8ClampedArray` 物件處理從 `XmlHttpRequest` 取得的二進位資料：  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 範例  
 下列範例顯示值在 `Uint8ClampedArray` 中的限制方式。  
  
```javascript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## 範例  
 下列範例顯示值在 `Uint8ClampedArray` 中的四捨五入方式。  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 11 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## 需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 請參閱  
 [Uint8Array 物件](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md)