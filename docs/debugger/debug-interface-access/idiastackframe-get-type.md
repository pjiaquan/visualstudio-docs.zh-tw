---
title: "IDiaStackFrame::get_type | Microsoft Docs"
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
  - "IDiaStackFrame::get_type 方法"
ms.assetid: 99daa97b-5c05-455d-bd1e-800762ccf7c9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_type
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的框架類型。  
  
## 語法  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回值，從[StackFrameTypeEnum 列舉](../../debugger/debug-interface-access/stackframetypeenum.md)列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`不支援的屬性。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [StackFrameTypeEnum 列舉](../../debugger/debug-interface-access/stackframetypeenum.md)