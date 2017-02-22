---
title: "IDiaEnumDebugStreams::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::Next 方法"
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的列舉型別序列中的偵錯資料流數。  
  
## 語法  
  
```cpp#  
HRESULT Next (   
   ULONG                     celt,   
   IDiaEnumDebugStreamData** rgelt,  
   ULONG*                    pceltFetched  
);  
```  
  
#### 參數  
 celt  
 \[in\] **t**他的偵錯資料流擷取列舉值中的數字。  
  
 rgelt  
 \[\] out傳回陣列的[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)物件，表示偵錯資料流擷取。  
  
 pceltFetched  
 \[\] out傳回偵錯傳回的資料流數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果沒有更多資料流。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)