---
title: "JsBackgroundWorkItemCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsBackgroundWorkItemCallback Typedef
背景工作項目回呼。  
  
## 語法  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### 參數  
 callbackData  
 傳遞給執行緒服務的資料引數。  
  
## 備註  
 這會傳遞給主機的執行緒服務 \(如果提供的話\)，讓主機可以在選擇的背景執行緒上叫用工作項目回呼。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)