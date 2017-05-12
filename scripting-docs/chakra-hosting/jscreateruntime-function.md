---
title: "JsCreateRuntime 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateRuntime"
helpviewer_keywords: 
  - "JsCreateRuntime 函式"
ms.assetid: 92d09b89-6593-4d73-a562-88f9fec10228
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateRuntime 函式
建立新的執行階段。  
  
## 語法  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_ JsRuntimeVersion version,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### 參數  
 `attributes`  
 要建立之執行階段的屬性。  
  
 `version`  
 要建立之執行階段的版本。  
  
 `threadService`  
 執行階段的執行緒服務。  可以是 null。  
  
 `runtime`  
 建立的執行階段。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 邊緣模式不支援 `version` 參數。  如需有關在邊緣模式中使用此 API 的詳細資訊，請參閱[以 Edge 和舊版引擎為目標](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)