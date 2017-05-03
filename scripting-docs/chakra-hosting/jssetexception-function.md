---
title: "JsSetException 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetException"
helpviewer_keywords: 
  - "JsSetException 函式"
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetException 函式
將目前內容的執行階段設定為例外狀況狀態。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### 參數  
 `exception`  
 要針對目前內容的執行階段設定的 JavaScript 例外狀況。  
  
## 傳回值  
 如果引擎設定為例外狀況狀態，則為 `JsNoError`，否則為失敗碼。  
  
## 備註  
 如果目前內容的執行階段已處於例外狀況狀態，此 API 就會傳回 `JsErrorInExceptionState`。  
  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)