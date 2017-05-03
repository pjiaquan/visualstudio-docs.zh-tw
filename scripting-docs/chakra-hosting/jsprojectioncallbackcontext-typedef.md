---
title: "JsProjectionCallbackContext Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsProjectionCallbackContext Typedef
從 JsRT 傳入應用程式回呼 JsProjectionEnqueueCallback，然後再以正確執行緒上的應用程式所提供的回呼 `JsProjectionCallback` 傳回 JsRT 的內容。  
  
## 語法  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## 備註  
 需要呼叫 `JsSetProjectionEnqueueCallback` 接收回呼。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)