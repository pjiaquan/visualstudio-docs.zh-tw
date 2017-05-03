---
title: "JsDisableRuntimeExecution 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisableRuntimeExecution"
helpviewer_keywords: 
  - "JsDisableRuntimeExecution 函式"
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDisableRuntimeExecution 函式
暫停指令碼執行，並在執行階段中終止任何執行中的指令碼。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### 參數  
 `runtime`  
 要暫停的執行階段。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 已暫停的執行階段之呼叫將會失敗，除非 `JsEnableRuntimeExecution` 被呼叫。  
  
 在執行階段為作用中的執行緒上未必需要呼叫這個應用程式開發介面。  雖然執行階段將設定為暫停狀態，但執行中的指令碼可能不會立即遭到暫停；將會盡快以不可攔截的例外狀況終止執行中的指令碼。  
  
 在早已暫停之執行階段的暫停中執行會沒有任何作業。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)