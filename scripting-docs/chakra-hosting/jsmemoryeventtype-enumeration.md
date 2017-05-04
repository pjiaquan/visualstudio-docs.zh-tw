---
title: "JsMemoryEventType 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsMemoryEventType"
helpviewer_keywords: 
  - "JsMemoryEventType 列舉"
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsMemoryEventType 列舉
配置回呼事件類型。  
  
## 語法  
  
```  
enum JsMemoryEventType;  
```  
  
## 成員  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`JsMemoryAllocate`|表示記憶體配置的要求。|  
|`JsMemoryFailure`|表示失敗的配置事件。|  
|`JsMemoryFree`|表示記憶體釋放事件。|  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)