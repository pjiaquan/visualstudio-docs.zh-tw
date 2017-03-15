---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

傳回對應於C \+\+. AMP快速Stub函式的所有快速指標標記值。  
  
## 語法  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### 參數  
 `cnt`  
 \[in\] 輸出陣列 `pPointerTags`的大小。  
  
 `pcnt`  
 \[out\] 計算速度比C\+\+ AMP快速Stub函式指標的標記。  
  
 `pPointerTags`  
 \[out\] 填滿快速指標標記的 `DWORD` 陣列指標在C\+\+ AMP快速Stub函式值。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 備註  
 呼叫這個方法對應至. C \+\+ AMP快速Stub函式的 `IDiaSymbol` 介面。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)