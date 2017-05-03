---
title: "JsParseSerializedScript 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsParseSerializedScript"
helpviewer_keywords: 
  - "JsParseSerializedScript 函式"
ms.assetid: 40d0c7c4-fd5b-46ed-9e65-38c2db2fc859
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsParseSerializedScript 函式
剖析序列化的指令碼，並傳回代表該指令碼的函式。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### 參數  
 `script`  
 要剖析的指令碼。  
  
 `buffer`  
 序列化的指令碼。  
  
 `sourceContext`  
 此 Cookie 會識別可偵錯指令碼內容所使用的指令碼。  
  
 `sourceUrl`  
 指令碼的來源位置。  
  
 `result`  
 代表指令碼的函式。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 需要使用中指令碼內容。  
  
 指令碼引擎未在記憶體中保存緩衝區，因此您的程式碼必須讓緩衝區保持運作中，而且一直持續到緩衝區可以用來執行指令碼為止。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)