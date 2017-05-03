---
title: "JsParseSerializedScriptWithCallback 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a93ecfb-4b82-4a85-b24c-6816db2332ea
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsParseSerializedScriptWithCallback 函式
剖析序列化的指令碼，並傳回代表該指令碼的函式。 僅在需要時，才提供消極載入指令碼來源的能力。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_ JsValueRef * result  
);  
  
```  
  
#### 參數  
 `scriptLoadCallback`  
 需要載入指令碼的原始程式碼時才呼叫回呼。  
  
 `scriptUnloadCallback`  
 當不再需要序列化的指令碼和原始程式碼時才呼叫回呼。  
  
 `buffer`  
 序列化的指令碼。  
  
 `sourceContext`  
 此 Cookie 會識別可偵錯指令碼內容所使用的指令碼。 這個內容會傳遞至 scriptLoadCallback 和 scriptUnloadCallback。  
  
 `sourceUrl`  
 指令碼的來源位置。  
  
 `result`  
 代表指令碼的函式。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
  
> [!NOTE]
>  市集應用程式尚未提供這個應用程式開發介面。  
  
 需要使用中指令碼內容。  
  
 執行階段會一直保留在緩衝區，直到從緩衝區建立之任何函式的所有執行個體都被記憶體回收為止。  它接著會呼叫 scriptUnloadCallback，告知呼叫者現在可以安全釋放。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)