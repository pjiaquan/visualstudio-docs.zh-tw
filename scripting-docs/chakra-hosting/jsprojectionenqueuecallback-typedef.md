---
title: "JsProjectionEnqueueCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsProjectionEnqueueCallback Typedef
當預估 API 在不同於原始執行緒的執行緒上完成時，JsRT 所呼叫的應用程式回呼。  
  
## 語法  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### 參數  
 `jsCallback`  
 要在原始執行緒上叫用的回呼。  
  
 `jsContext`  
 應用程式內容。  
  
 `callbackState`  
 必須傳入 `jsCallback` 的 JsRT 內容。  
  
## 備註  
 需要呼叫 JsSetProjectionEnqueueCallback 接收回呼。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)