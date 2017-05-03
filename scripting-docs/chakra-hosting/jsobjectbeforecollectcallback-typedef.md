---
title: "JsObjectBeforeCollectCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsObjectBeforeCollectCallback Typedef
收集物件前呼叫的回呼。  
  
## 語法  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### 參數  
 `ref`  
 要收集的物件。  
  
 `callbackState`  
 傳遞給 `JsSetObjectBeforeCollectCallback` 的狀態。  
  
## 備註  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)