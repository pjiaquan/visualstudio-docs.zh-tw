---
title: "JsRef Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRef Typedef
Chakra 記憶體回收行程擁有之物件的參考。  
  
## 語法  
  
```  
typedef void *JsRef;  
```  
  
## 備註  
 只要 JsRef 參考儲存在區域變數或參數中 \(也就是  在堆疊上\)，Chakra 執行階段便會自動追蹤這些參考。  如果將 JsRef 儲存在堆疊以外的位置，則需要呼叫 JsAddRef 和 JsRelease 來管理物件的存留期，否則記憶體回收行程可能會釋放仍在使用中的物件。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)