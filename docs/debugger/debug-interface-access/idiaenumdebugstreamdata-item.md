---
title: "IDiaEnumDebugStreamData::Item | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Item 方法"
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的記錄。  
  
## 語法  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 參數  
 Index \- 索引  
 \[in\]要擷取的資料錄的索引。  索引是以介於 0 到`count`\-1，其中`count`傳回的[IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md)。  
  
 cbData  
 \[in\]資料緩衝區的大小，以位元組為單位。  
  
 pcbData  
 \[\] out傳回動作傳回的位元組數目。  如果`data`是`NULL`，然後`pcbData`包含在指定的記錄，您可以使用資料的位元組總數。  
  
 資料\]  
 \[\] out在以偵錯資料流的資料錄資料填滿的緩衝區。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_INVALIDARG`無效的參數，則為由右`index`參數超出界限。  
  
## 請參閱  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md)   
 [IDiaEnumDebugStreamData::Skip](../Topic/IDiaEnumDebugStreamData::Skip.md)