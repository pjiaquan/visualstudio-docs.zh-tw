---
title: "JsSerializedScriptLoadSourceCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptLoadSourceCallback Typedef
由執行階段呼叫，以載入序列化指令碼的原始程式碼。 在 `JsSerializedScriptUnloadCallback` 之前，呼叫端都必須確保指令碼緩衝區有效。  
  
## 語法  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### 參數  
 `sourceContext`  
 傳遞至 `JsParseSerializedScriptWithCallback` 或 `JsRunSerializedScriptWithCallback` 的內容。  
  
 `scriptBuffer`  
 傳回的指令碼。  
  
## 備註  
  
> [!WARNING]
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)