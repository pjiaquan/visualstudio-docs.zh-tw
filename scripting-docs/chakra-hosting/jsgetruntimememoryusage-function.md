---
title: "JsGetRuntimeMemoryUsage 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetRuntimeMemoryUsage"
helpviewer_keywords: 
  - "JsGetRuntimeMemoryUsage 函式"
ms.assetid: b9bd4146-bfbc-4cb1-a0e9-a0ded7fb09bd
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetRuntimeMemoryUsage 函式
取得執行階段目前的記憶體使用量。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryUsage(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryUsage  
);  
```  
  
#### 參數  
 `runtime`  
 要擷取其記憶體使用量的執行階段。  
  
 `memoryUsage`  
 執行階段目前的記憶體使用量，以位元組為單位。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 不論執行階段是否作用於另一個執行緒上，總是可以擷取記憶體使用量。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)