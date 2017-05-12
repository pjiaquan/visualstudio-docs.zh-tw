---
title: "JsGetRuntimeMemoryLimit 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsGetRuntimeMemoryLimit 函式"
ms.assetid: ed81ca60-99fd-46b0-89ae-f6ac07926904
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetRuntimeMemoryLimit 函式
取得執行階段目前的記憶體限制。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryLimit  
);  
```  
  
#### 參數  
 `runtime`  
 要擷取其記憶體限制的執行階段。  
  
 `memoryLimit`  
 執行階段目前的記憶體限制 \(以位元組為單位\)，若沒有設定限制則為 \-1。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 不論執行階段是否作用於另一個執行緒上，一律可以擷取該執行階段的記憶體限制。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)