---
title: "JsCreateDataView 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateDataView 函式
建立 JavaScript `DataView` 物件。  
  
## 語法  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### 參數  
 `arrayBuffer`  
 要做為結果 `DataView` 物件儲存體的現有 `ArrayBuffer` 物件。  
  
 `byteOffset`  
 結果 `DataView` 所要參考之 `arrayBuffer` 開頭的位移 \(以位元組為單位\)。  
  
 `byteLength`  
 結果 DataView 所要參考之 ArrayBuffer 中的位元組數目。  
  
 `result`  
 新的 DataView 物件。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)