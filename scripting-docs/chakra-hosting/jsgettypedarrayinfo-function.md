---
title: "JsGetTypedArrayInfo 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsGetTypedArrayInfo 函式
取得具類型陣列的常用屬性。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### 參數  
 `typedArray`  
 具類型陣列執行個體。  
  
 `arrayType`  
 陣列的類型。  
  
 `arrayBuffer`  
 陣列的  Backstore。  
  
 `byteOffset`  
 從陣列所參考之 arrayBuffer 開頭處算起的位元組位移。  
  
 `byteLength`  
 陣列中的位元組數目。  
  
## 傳回值  
 如果作業成功，則為  碼，否則為失敗碼。  
  
## 備註  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)