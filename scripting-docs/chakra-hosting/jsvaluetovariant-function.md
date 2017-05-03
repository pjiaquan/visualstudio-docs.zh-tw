---
title: "JsValueToVariant 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueToVariant"
helpviewer_keywords: 
  - "JsValueToVariant 函式"
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsValueToVariant 函式
初始化傳入的 `VARIANT`，做為 JavaScript 值的投影。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### 參數  
 `object`  
 要投影為 `VARIANT` 的 JavaScript 值。  
  
 `variant`  
 要初始化為投影的 `VARIANT` 結構之指標。  
  
## 傳回值  
  
## 備註  
 COM Automation 用戶端可以使用 `VARIANT` 投影呼叫投影的 JavaScript 物件。  
  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)