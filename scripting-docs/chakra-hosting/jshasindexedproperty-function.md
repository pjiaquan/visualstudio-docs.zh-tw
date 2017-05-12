---
title: "JsHasIndexedProperty 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasIndexedProperty"
helpviewer_keywords: 
  - "JsHasIndexedProperty 函式"
ms.assetid: 30436a3d-fda0-407e-aba2-142be2310372
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsHasIndexedProperty 函式
測試物件是否具有位於指定索引處的值。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsHasIndexedProperty(  
   _In_ JsValueRef object,  
   _In_ JsValueRef index,  
   _Out_ bool *result  
);  
```  
  
#### 參數  
 `object`  
 要處理的物件。  
  
 `index`  
 要測試的索引。  
  
 `result`  
 物件是否具有位於指定索引處的值。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)