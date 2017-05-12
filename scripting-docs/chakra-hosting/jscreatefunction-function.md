---
title: "JsCreateFunction 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateFunction"
helpviewer_keywords: 
  - "JsCreateFunction 函式"
ms.assetid: b298a96a-5ef7-4203-a8c8-55f9bfc6d2bb
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsCreateFunction 函式
建立新的 JavaScript 函式。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsCreateFunction(  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### 參數  
 `nativeFunction`  
 叫用函式時呼叫的方法。  
  
 `callbackState`  
 將回傳給回呼的使用者提供狀態。  
  
 `function`  
 新的函式物件。  
  
## 傳回值  
 呼叫的結果 \(如果有的話\)。  
  
## 備註  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)