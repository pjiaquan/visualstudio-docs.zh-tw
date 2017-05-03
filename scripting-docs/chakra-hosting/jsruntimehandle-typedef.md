---
title: "JsRuntimeHandle Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRuntimeHandle Typedef
Chakra 執行階段的控制代碼。  
  
## 語法  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## 備註  
 每個 Chakra 執行階段都有自己的獨立執行引擎、JIT 編譯器和記憶體回收堆積。  因此，每個執行階段會與其他執行階段完全隔離。  
  
 執行階段可用於任何執行緒上，但一次只能有一個執行緒呼叫執行階段。  
  
> [!WARNING]
>  JsRuntimeHandle 與 Chakra 裝載應用程式開發介面中的其他物件參考不同，由於它本身即包含記憶體回收堆積，因此不會進行記憶體回收。  執行階段會繼續存在，直到呼叫 JsDisposeRuntime 為止。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)