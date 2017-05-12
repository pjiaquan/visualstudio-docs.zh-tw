---
title: "JsIsRuntimeExecutionDisabled 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsRuntimeExecutionDisabled"
helpviewer_keywords: 
  - "JsIsRuntimeExecutionDisabled 函式"
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsIsRuntimeExecutionDisabled 函式
傳回值，指出執行階段中是否已停用指令碼執行。  
  
## 語法  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(  
    _In_ JsRuntimeHandle runtime,  
    _Out_ bool *isDisabled  
);  
```  
  
#### 參數  
 `runtime`  
 指定執行階段檢查是否已停用執行。  
  
 `isDisabled`  
 如果已停用執行，則為 `true`，否則為 `false`。  
  
## 傳回值  
 如果作業成功則為 `JsNoError`，否則為失敗碼。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)