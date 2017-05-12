---
title: "JsHasException 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasException"
helpviewer_keywords: 
  - "JsHasException 函式"
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsHasException 函式
判斷目前內容的執行階段是否處於例外狀況狀態。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### 參數  
 `hasException`  
 判斷目前內容的執行階段是否處於例外狀況狀態。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 如果呼叫執行階段會導致例外狀況 \(因為執行指令碼或是例如轉換失敗\)，則會將執行階段放入「例外狀況狀態」。 對執行階段建立之任何內容的所有呼叫 \(例外狀況 API 除外\) 都會失敗並具有 `JsErrorInExceptionState`，直到清除例外狀況為止。  
  
 如果回呼傳回至引擎時，目前內容的執行階段處於例外狀況狀態，引擎會自動重新擲回例外狀況。  
  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)