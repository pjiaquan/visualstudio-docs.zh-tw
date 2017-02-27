---
title: "IDiaEnumStackFrames::Next | Microsoft Docs"
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
  - "IDiaEnumStackFrames::Next 方法"
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取列舉型別序列中的指定的數目的堆疊框架項目。  
  
## 語法  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### 參數  
 celt  
 \[in\]要擷取的列舉值中的 stackframe 項目數目。  
  
 rgelt  
 \[\] out要填入要求陣列[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)物件。  
  
 pceltFetched  
 \[\] out傳回的堆疊框架項目中擷取的列舉值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果沒有更多的堆疊框架。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)