---
title: "JsAddRef 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsAddRef"
helpviewer_keywords: 
  - "JsAddRef 函式"
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsAddRef 函式
加入記憶體回收物件的參考。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### 參數  
 `ref`  
 要加入參考的物件。  
  
 `count`  
 物件的新參考次數 \(可以傳入 Null\)。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 這只需要在 `JsRef` 控制代碼上呼叫，這些控制代碼不會儲存在堆疊的某個地方。  呼叫 `JsAddRef` 可確保 `JsRef` 所指的物件不會在呼叫 `JsRelease` 之前釋放。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)