---
title: "JsCreateContext 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateContext"
helpviewer_keywords: 
  - "JsCreateContext 函式"
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateContext 函式
建立執行指令碼的指令碼內容。  
  
## 語法  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### 參數  
 `runtime`  
 正在其中建立指令碼內容的執行階段。  
  
 `debugApplication`  
 用於偵錯的偵錯應用程式。  這個參數可以是 null，在此情況下不會啟用內容的偵錯。  
  
 `newContext`  
 已建立的指令碼內容。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 每個指令碼內容都有它自己的全域物件，且與所有其他指令碼內容隔離。  
  
 邊緣模式不支援 `debugApplication` 參數。  如需有關在邊緣模式中使用此 API 的詳細資訊，請參閱[以 Edge 和舊版引擎為目標](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)