---
title: "JsSetRuntimeBeforeCollectCallback 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeBeforeCollectCallback"
helpviewer_keywords: 
  - "JsSetRuntimeBeforeCollectCallback 函式"
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeBeforeCollectCallback 函式
設定在記憶體回收之前執行階段所呼叫的回呼函式。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### 參數  
 `runtime`  
 要為其註冊配置回呼的執行階段。  
  
 `callbackState`  
 將回傳給回呼的使用者提供狀態。  
  
 `beforeCollectCallback`  
 正在設定的回呼函式。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 會在目前執行階段的執行緒上叫用此回呼，因此直到完成回呼之前會封鎖執行。  
  
 回呼可以由主機用來準備記憶體回收。  例如，藉由釋放 Chakra 物件上不必要的參考。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)