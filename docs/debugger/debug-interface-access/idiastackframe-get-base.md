---
title: "IDiaStackFrame::get_base | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackFrame::get_base 方法"
ms.assetid: f27477d7-26fe-4c1c-a08a-c52cb20c8293
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_base
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取框架的基底位址。  
  
## 語法  
  
```cpp#  
HRESULT get_base (   
   ULONGLONG* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的基底位址。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`不支援的屬性。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)