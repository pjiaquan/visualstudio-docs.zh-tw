---
title: "JsPromiseContinuationCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsPromiseContinuationCallback Typedef
承諾接續回呼。  
  
## 語法  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### 參數  
 `task`  
  `callbackState`  
  
## 備註  
 主機可以在 `JsSetPromiseContinuationCallback` 中指定承諾接續回呼。 如果指令碼建立一個要在稍後執行的工作，則會使用該工作呼叫承諾接續回呼，並且應該將該工作放在 FIFO 佇列中，以在目前指令碼完成執行時接著執行。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)