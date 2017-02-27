---
title: "IDiaStackFrame::get_lengthParams | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaStackFrame::get_lengthParams 方法"
ms.assetid: 78005efa-2883-4823-b4e4-711a66672c78
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_lengthParams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的推入堆疊的參數的位元組數目。  
  
## 語法  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的參數的位元組數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`不支援的屬性。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)