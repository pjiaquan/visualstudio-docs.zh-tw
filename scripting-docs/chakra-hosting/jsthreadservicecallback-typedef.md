---
title: "JsThreadServiceCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsThreadServiceCallback Typedef
執行緒服務回呼。  
  
## 語法  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### 參數  
 callback  
 背景工作項目的回呼。  
  
 callbackData  
 傳遞給回呼的資料引數。  
  
## 備註  
 當主機呼叫 JsCreateRuntime 時，可指定背景執行緒服務。  如果指定，則會將背景工作項目傳遞給使用這個回呼的主機。  主機必須立即開始執行背景工作項目並傳回 true，或傳回 false，執行階段將處理執行緒中的工作項目。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)