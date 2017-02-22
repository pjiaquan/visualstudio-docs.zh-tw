---
title: "IDiaEnumDebugStreams::Skip | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::Skip 方法"
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

略過指定的數目的列舉型別序列中的偵錯資料流。  
  
## 語法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 參數  
 `celt`  
 \[in\]略過列舉序列中的偵錯資料流數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`如果沒有更多的記錄，略過。  
  
## 請參閱  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)