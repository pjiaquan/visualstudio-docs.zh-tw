---
title: "JsCreateExternalArrayBuffer 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsCreateExternalArrayBuffer 函式
建立 Javascript `ArrayBuffer` 物件來存取外部記憶體。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### 參數  
 `data`  
 外部記憶體的指標。  
  
 `byteLength`  
 外部記憶體中的位元組數目。  
  
 `finalizeCallback`  
 物件完成時的回呼。 可能是 Null。  
  
 `callbackState`  
 將回傳給 finalizeCallback 的使用者提供狀態。  
  
 `result`  
 新的 `ArrayBuffer` 物件。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)