---
title: "JsSetProjectionEnqueueCallback 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsSetProjectionEnqueueCallback 函式
設定要用來叫用預估完成以回到要求執行緒之呼叫端的回呼。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### 參數  
 `projectionEnqueueContext`  
 當背景執行緒上發生預估完成時，便會叫用這個回呼。  
  
 `callbackState`  
 提供給 `projectionEnqueueContext` 的應用程式內容。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 需要使用中指令碼內容。  
  
 呼叫應該來自不同的 COM Apartment，或來自相同 MTA 中的不同執行緒。  
  
 只有邊緣模式才支援這個 API。  
  
> [!CAUTION]
>  這個 API 目前不支援 PInvoke。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)