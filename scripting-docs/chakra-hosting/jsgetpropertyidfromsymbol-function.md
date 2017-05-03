---
title: "JsGetPropertyIdFromSymbol 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 190fe4b9-352e-4b10-9d0e-6c6bbd6363e8
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetPropertyIdFromSymbol 函式
取得與符號關聯的屬性 ID。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromSymbol(  
   _In_ JsValueRef symbol,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### 參數  
 `symbol`  
 正在擷取其屬性 ID 的符號。  
  
 `propertyId`  
 指定符號的屬性 ID。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 內容有專用的屬性 ID，因此不可跨內容使用。  
  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)