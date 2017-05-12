---
title: "JsStopProfiling 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStopProfiling"
helpviewer_keywords: 
  - "JsStopProfiling 函式"
ms.assetid: 3639c04f-a0f9-418b-be39-92f64b4e7ef8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsStopProfiling 函式
在目前的內容中停止程式碼剖析。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsStopProfiling(  
   _In_ HRESULT reason  
);  
```  
  
#### 參數  
 `reason`  
 停止程式碼剖析是為了傳遞分析工具的回呼。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 如果程式碼剖析尚未開始，則不會傳回錯誤。  
  
 需要使用中指令碼內容。  
  
 桌面應用程式中支援這個 API，但是在市集應用程式中不支援。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)