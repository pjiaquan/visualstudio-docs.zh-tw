---
title: "JsStringToPointer 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStringToPointer"
helpviewer_keywords: 
  - "JsStringToPointer 函式"
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsStringToPointer 函式
擷取字串值的字串指標。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### 參數  
 `value`  
 要轉換成字串指標的字串值。  
  
 `stringValue`  
 字串指標。  
  
 `stringLength`  
 字串的長度。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 此函式可擷取字串值的字串指標。  如果值的類型不是字串，它將會失敗並傳回 `JsErrorInvalidArgument`。  傳回字串的存留期和其來源值的存留期相同，不過系統不會將字串指標視為值的參考 \(因此將無法收集保留\)。  
  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)