---
title: "JsGetTypedArrayStorage 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetTypedArrayStorage 函式
取得具類型陣列所使用的基礎記憶體儲存體。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### 參數  
 `typedArray`  
 具類型陣列執行個體。  
  
 `buffer`  
 陣列的緩衝區。  傳回的緩衝區存留期與陣列的存留期相同。  用於記憶體回收的緩衝區指標不是陣列的參考。  
  
 `bufferLength`  
 緩衝區中的位元組數目。  
  
 `arrayType`  
 陣列的類型。  
  
 `elementSize`  
 陣列的項目大小。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)