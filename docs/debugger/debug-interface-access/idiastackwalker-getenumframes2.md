---
title: "IDiaStackWalker::getEnumFrames2 | Microsoft Docs"
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
  - "IDiaStackWalker2::getEnumFrames2 方法"
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取特定的平台類型的堆疊框架列舉器。  
  
## 語法  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### 參數  
 `cpuid`  
 \[in\]介於[CV\_CPU\_TYPE\_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md) ，指定列舉型別平台類型。  
  
 `pHelper`  
 \[in\]協助人員[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)物件。  
  
 `ppEnum`  
 \[\] out傳回[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)物件，其中包含一份[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 若要取得建立堆疊框架的清單只是 x86 平台，呼叫[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)方法。  
  
## 請參閱  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV\_CPU\_TYPE\_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)