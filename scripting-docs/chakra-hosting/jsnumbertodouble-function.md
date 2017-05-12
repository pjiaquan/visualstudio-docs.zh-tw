---
title: "JsNumberToDouble 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsNumberToDouble"
helpviewer_keywords: 
  - "JsNumberToDouble 函式"
ms.assetid: 5f52e8b6-2b70-49a3-879a-bd83ebf2ac33
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsNumberToDouble 函式
擷取數值的`double` 值。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsNumberToDouble(  
   _In_ JsValueRef value,  
   _Out_ double *doubleValue  
);  
```  
  
#### 參數  
 `value`  
 要轉換成 `double` 值的數值。  
  
 `doubleValue`  
 `double` 值。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 此函式會擷取數值的值。  如果值的類型不是數字，它將會失敗並傳回 `JsErrorInvalidArgument`。  
  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)