---
title: "JsNumberToInt 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsNumberToInt 函式
擷取數值的 `int` 值。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### 參數  
 `value`  
 要轉換成 `int` 值的數值。  
  
 `intValue`  
 `int` 值。  
  
## 傳回值  
  
## 備註  
 這個函式會擷取數值的值，並轉換成 `int` 值。  如果值的類型不是數字，它將會失敗並傳回 `JsErrorInvalidArgument`。  
  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)