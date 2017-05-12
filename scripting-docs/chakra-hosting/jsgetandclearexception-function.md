---
title: "JsGetAndClearException 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetAndClearException"
helpviewer_keywords: 
  - "JsGetAndClearException 函式"
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetAndClearException 函式
傳回造成目前內容執行階段處於例外狀況狀態的例外狀況，並重設該執行階段的例外狀況狀態。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### 參數  
 `exception`  
 目前內容的執行階段之例外狀況。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 如果目前內容的執行階段未處於例外狀況狀態，此 API 就會傳回 `JsErrorInvalidArgument`。  如果停用執行階段，這將傳回表示指令碼已被終止的例外狀況，但它將不會清除此例外狀況 \(若該執行階段使用 `JsEnableRuntimeExecution` 以重新啟用，則例外狀況將被清除\)。  
  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)