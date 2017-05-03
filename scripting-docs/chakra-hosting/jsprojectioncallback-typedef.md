---
title: "JsProjectionCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsProjectionCallback Typedef
應該使用傳遞給正確執行緒上 `JsProjectionEnqueueCallback` 之內容呼叫的 JsRT 回呼。  
  
## 語法  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### 參數  
 `jsContext`  
 需要呼叫 `JsSetProjectionEnqueueCallback` 接收回呼。  
  
## 備註  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)