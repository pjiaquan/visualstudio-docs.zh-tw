---
title: "IDiaEnumDebugStreamData::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Next 方法"
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的指定列舉序列中的記錄筆數。  
  
## 語法  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### 參數  
 celt  
 \[in\]要擷取的資料錄數目。  
  
 cbData  
 \[in\]資料緩衝區的大小，以位元組為單位。  
  
 pcbData  
 \[\] out傳回動作傳回的位元組數目。  如果`data` ，是 NULL， `pcbData`的所有要求的記錄包含的可用資料的位元組總數。  
  
 資料\]  
 \[\] out要填滿偵錯資料流記錄資料的緩衝區。  
  
 pceltFetched  
 輸入 \[、 輸出\]傳回的記錄號碼`data`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果沒有更多的記錄。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)