---
title: "Uint8Array 物件 | Microsoft Docs"
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
ms.assetid: ae78b3ee-b660-4625-ac7b-d414a0842c87
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Uint8Array 物件
8 位元不帶正負號整數值的類型陣列。  內容已初始化為 0。  如果無法配置要求的位元組數目，就會引發例外狀況。  
  
## 語法  
  
```  
  
      uint8Array = new Uint8Array( length );  
uint8Array = new Uint8Array( array );  
uint8Array = new Uint8Array( buffer, byteOffset, length);  
```  
  
## 參數  
 `uint8Array`  
 必要項。  要對其指派 **Uint8Array** 物件的變數名稱。  
  
 `length`  
 指定陣列中元素的數目。  
  
 `array`  
 這個陣列中所包含的陣列 \(或類型陣列\)。  內容會初始化為所指陣列或類型陣列的內容，其中每個元素都會轉換成 Uint8 類型。  
  
 `buffer`  
 Uint8Array 代表的 ArrayBuffer。  
  
 `byteOffset`  
 選擇項。  以位元組為單位，指定從緩衝區開頭 \(也就是 Uint8Array 應該開始的位置\) 算起的位移。  
  
 `length`  
 陣列中的元素數目。  
  
## 常數  
 下表列出 `Uint8Array` 物件的常數。  
  
|常數|描述|  
|--------|--------|  
|[BYTES\_PER\_ELEMENT 常數](../../javascript/reference/bytes-per-element-constant-uint8array.md)|陣列中每個元素的大小 \(以位元組為單位\)。|  
  
## 屬性  
 下表列出 `Uint8Array` 物件的常數。  
  
|屬性|描述|  
|--------|--------|  
|[buffer 屬性](../../javascript/reference/buffer-property-uint8array.md)|唯讀。  取得這個陣列所參考的 ArrayBuffer。|  
|[byteLength 屬性](../../javascript/reference/bytelength-property-uint8array.md)|唯讀。  這個陣列從其 ArrayBuffer 開頭算起的長度 \(以位元組為單位\)，在建構階段長度都不會改變。|  
|[byteOffset 屬性](../../javascript/reference/byteoffset-property-uint8array.md)|唯讀。  這個陣列從其 ArrayBuffer 開頭算起的位移 \(以位元組為單位\)，在建構階段位移都不會改變。|  
|[length 屬性](../../javascript/reference/length-property-uint8array.md)|陣列的長度。|  
|||  
  
## 方法  
 下表列出 `Uint8Array` 物件的方法。  
  
|方法|描述|  
|--------|--------|  
|[set 方法 \(Uint8Array\)](../../javascript/reference/set-method-uint8array.md)|設定一個值或值陣列。|  
|[subarray 方法 \(Uint8Array\)](../../javascript/reference/subarray-method-uint8array.md)|為這個陣列取得 ArrayBuffer 存放區的新 Uint8Array 檢視。|  
  
## 範例  
 下列範例將示範如何使用 Uint8Array 物件來處理從 XmlHttpRequest 取得的二進位資料：  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]