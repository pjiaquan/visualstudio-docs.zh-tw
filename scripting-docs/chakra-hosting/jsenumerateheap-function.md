---
title: "JsEnumerateHeap 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEnumerateHeap"
helpviewer_keywords: 
  - "JsEnumerateHeap 函式"
ms.assetid: 3e518e0b-b959-4686-899c-83e6b1946c9d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsEnumerateHeap 函式
列舉目前內容的堆積。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsEnumerateHeap(  
   _Out_ IActiveScriptProfilerHeapEnum **enumerator  
);  
```  
  
#### 參數  
 `enumerator`  
 堆積的列舉程式。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 正在列舉堆積時無法移除目前的內容，而且除非已釋放堆積列舉程式，否則所有用來修改內容狀態的呼叫將會失敗。  
  
 需要使用中指令碼內容。  
  
 桌面應用程式中支援這個 API，但是在市集應用程式中不支援。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)