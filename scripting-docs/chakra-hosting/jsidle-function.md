---
title: "JsIdle 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIdle"
helpviewer_keywords: 
  - "JsIdle 函式"
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsIdle 函式
告知執行階段執行任何必要的閒置處理。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### 參數  
 `nextIdleTick`  
 當需要執行更多閒置作業時，下個系統會繼續進行滴答。  可以是 null。  如果沒有近期的閒置工作需要執行，則傳回滴答的最大數目。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 如果已為目前的執行階段啟用閒置處理，則呼叫 `JsIdle` 會通知目前的執行階段主機處於閒置狀態，並通知執行階段可以執行記憶體清除工作。  
  
 直到執行階段有更多閒置工作需執行之前，`JsIdle` 也可以傳回系統滴答次數。  在滴答次數傳遞之前呼叫的 `JsIdle` 將無法執行。  
  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)