---
title: "JsContextRef Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsContextRef Typedef
指令碼內容的參考。  
  
## 語法  
  
```  
typedef JsRef JsContextRef;  
```  
  
## 備註  
 每個指令碼內容都含有自己的全域物件，該物件與其他指令碼內容中的全域物件不同。  
  
 許多 Chakra 裝載應用程式開發介面需要「使用中」指令碼內容，您可以使用 `JsSetCurrentContext` 來設定此內容。  需要設定目前內容的 Chakra 裝載應用程式開發介面，會在其文件中明確註明。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)