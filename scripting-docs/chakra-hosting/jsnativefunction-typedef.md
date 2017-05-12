---
title: "JsNativeFunction Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsNativeFunction Typedef
函式回呼。  
  
## 語法  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### 參數  
 被呼叫端  
 `Function` 物件，代表所叫用的函式。  
  
 isConstructCall  
 指出這是一般呼叫，還是 'new' 呼叫。  
  
 引數  
 要呼叫的引數。  
  
 argumentCount  
 引數數目。  
  
## 屬性值\/傳回值  
 呼叫的結果 \(如果有的話\)。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)