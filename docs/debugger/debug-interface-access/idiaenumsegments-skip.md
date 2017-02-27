---
title: "IDiaEnumSegments::Skip | Microsoft Docs"
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
  - "IDiaEnumSegments::Skip 方法"
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

略過指定的列舉型別序列的線段數目。  
  
## 語法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 參數  
 celt  
 \[in\]略過列舉序列中的線段數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`是否有沒有更多的區段，以略過。  
  
## 請參閱  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)