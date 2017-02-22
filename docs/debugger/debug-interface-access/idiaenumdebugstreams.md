---
title: "IDiaEnumDebugStreams | Microsoft Docs"
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
  - "IDiaEnumDebugStreams 介面"
ms.assetid: 611caf4f-7a5f-4aa4-b909-52feeb3cc752
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列舉各種資料來源中所包含的偵錯資料流。  
  
## 語法  
  
```  
IDiaEnumDebugStreams : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaEnumDebugStreams`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaEnumDebugStreams::get\_\_NewEnum](../Topic/IDiaEnumDebugStreams::get__NewEnum.md)|擷取`IEnumVARIANT`版的這個列舉值。|  
|[IDiaEnumDebugStreams::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md)|擷取偵錯資料流數目。|  
|[IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)|擷取的索引的偵錯資料流。|  
|[IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)|擷取指定的列舉型別序列中的偵錯資料流數。|  
|[IDiaEnumDebugStreams::Skip](../../debugger/debug-interface-access/idiaenumdebugstreams-skip.md)|略過指定的數目的列舉型別序列中的偵錯資料流。|  
|[IDiaEnumDebugStreams::Reset](../../debugger/debug-interface-access/idiaenumdebugstreams-reset.md)|將列舉型別序列重設至開頭。|  
|[IDiaEnumDebugStreams::Clone](../../debugger/debug-interface-access/idiaenumdebugstreams-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
  
## 備註  
 偵錯資料流的內容取決於實作，也未記載的資料格式。  
  
## 呼叫者的備忘稿  
 呼叫[IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)方法，以取得`IDiaEnumDebugStreams`物件。  
  
## 範例  
 這個範例會示範如何從這個介面存取可用的資料流。  請參閱[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)介面的實作`PrintStreamData`函式。  
  
```cpp#  
void DumpAllDebugStreams( IDiaSession* pSession)  
{  
    IDiaEnumDebugStreams* pEnumStreams;  
  
    wprintf(L"\n\n*** DEBUG STREAMS\n\n");  
    // Retrieve an enumerated sequence of debug data streams  
    if(pSession->getEnumDebugStreams(&pEnumStreams) == S_OK)  
    {  
        IDiaEnumDebugStreamData* pStream;  
        ULONG celt = 0;  
  
        for(; pEnumStreams->Next(1, &pStream, &celt) == S_OK; pStream = NULL)  
        {  
            PrintStreamData(pStream);  
            pStream->Release();  
        }  
        pEnumStreams->Release();  
    }  
    else  
    {  
      wprintf(L"Failed to get any debug streams!\n");  
    }  
    wprintf(L"\n");  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)