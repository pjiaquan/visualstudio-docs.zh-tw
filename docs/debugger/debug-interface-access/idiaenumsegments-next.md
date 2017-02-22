---
title: "IDiaEnumSegments::Next | Microsoft Docs"
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
  - "IDiaEnumSegments::Next 方法"
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的列舉型別序列中的區段數目。  
  
## 語法  
  
```cpp#  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### 參數  
 celt  
 \[in\]要擷取列舉值中的線段數目。  
  
 rgelt  
 \[\] out陣列是以您想要填滿[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)表示該區段的物件。  
  
 pceltFetched  
 \[\] out傳回已擷取的列舉值的線段數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果沒有更多的區段。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)