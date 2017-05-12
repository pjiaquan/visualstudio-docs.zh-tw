---
title: "JsSerializedScriptUnloadCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptUnloadCallback Typedef
由執行階段在完成與指令碼執行相關的所有資源時呼叫。 呼叫端應該釋放載入的任何來源、位元組碼和目前的內容。  
  
## 語法  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### 參數  
 `sourceContext`  
 傳遞至 `JsParseSerializedScriptWithCallback` 或 `JsRunSerializedScriptWithCallback` 的內容。  
  
## 備註  
  
> [!WARNING]
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)