---
title: "JsMemoryAllocationCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# JsMemoryAllocationCallback Typedef
使用者針對記憶體配置事件實作的回呼常式。  
  
## 語法  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### 參數  
 callbackState  
 傳遞給 JsSetRuntimeMemoryAllocationCallback 的狀態。  
  
 allocationEvent  
 類型配置事件的類型。  
  
 allocationSize  
 配置的大小。  
  
## 屬性值\/傳回值  
 若為 JsMemoryAllocate 事件，傳回 true 可讓執行階段繼續配置；  傳回 false 表示拒絕配置要求。  已忽略其他配置事件的傳回值。  
  
## 備註  
 使用 JsSetRuntimeMemoryAllocationCallback 註冊這個回呼。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)