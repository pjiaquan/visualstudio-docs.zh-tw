---
title: "JsSerializeScript 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSerializeScript"
helpviewer_keywords: 
  - "JsSerializeScript 函式"
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSerializeScript 函式
將已剖析的指令碼序列化至緩衝區以重複使用。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### 參數  
 `script`  
 要序列化的指令碼。  
  
 `buffer`  
 要放入序列化指令碼的緩衝區。  可以是 null。  
  
 `bufferSize`  
 容納序列化指令碼所需的緩衝區；亦即進入時，緩衝區的大小 \(以位元組為單位\)；結束時，緩衝區的大小 \(以位元組為單位\)。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 `JsSerializeScript` 會剖析指令碼，然後將指令碼的已剖析形式儲存為與執行階段無關的格式。  這麼一來，序列化的指令碼即可在任何執行階段還原序列化，而不需重新剖析指令碼。  
  
 需要使用中指令碼內容。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)