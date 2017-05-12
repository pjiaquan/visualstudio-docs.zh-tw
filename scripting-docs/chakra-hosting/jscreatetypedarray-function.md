---
title: "JsCreateTypedArray 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateTypedArray 函式
建立 JavaScript 具類型陣列物件。  
  
## 語法  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### 參數  
 `arrayType`  
 要建立之陣列的類型。  
  
 `baseArray`  
 新陣列的基底陣列。  如果沒有基底陣列，則使用 `JS_INVALID_REFERENCE`。  
  
 `byteOffset`  
 結果具類型陣列所要參考之 `baseArray` \(`ArrayBuffer`\) 開頭的位移 \(以位元組為單位\)。  只有在 `baseArray` 是 `ArrayBuffer` 物件時才適用。  否則必須為 0。  
  
 `elementLength`  
 陣列中的元素數目。  只有在建立不具有 `baseArray` 的新具類型陣列 \(`baseArray` 是 `JS_INVALID_REFERENCE`\)，或 `baseArray` 是 `ArrayBuffer` 物件時才適用。  否則必須為 0。  
  
 `result`  
 新的具類型陣列物件。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 `baseArray` 可以是 `ArrayBuffer`、其他類型的陣列或 JavaScript `Array`。  如果傳回的具類型陣列是 `ArrayBuffer`，則會使用 `baseArray`；否則會建立並使用基礎來源陣列的複本。  
  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)