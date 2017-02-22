---
title: "IDiaEnumSourceFiles | Microsoft Docs"
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
  - "IDiaEnumSourceFiles 介面"
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSourceFiles
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列舉各種資料來源中所含的原始程式檔。  
  
## 語法  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaEnumSourceFiles`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaEnumSourceFiles::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|擷取`IEnumVARIANT Interface`版的這個列舉值。|  
|[IDiaEnumSourceFiles::get\_Count](../Topic/IDiaEnumSourceFiles::get_Count.md)|擷取原始程式檔數目。|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|擷取的索引的原始程式檔。|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|擷取指定的列舉型別序列中的原始程式檔。|  
|[IDiaEnumSourceFiles::Skip](../Topic/IDiaEnumSourceFiles::Skip.md)|略過指定的數目的列舉型別序列中的原始程式檔。|  
|[IDiaEnumSourceFiles::Reset](../Topic/IDiaEnumSourceFiles::Reset.md)|將列舉型別序列重設至開頭。|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
  
## 備註  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫`QueryInterface`上的方法[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件。  範例中的，如需詳細資訊，請參閱。  
  
## 範例  
 本範例示範如何取得`IDiaEnumSourceFiles` DIA 工作階段物件中的資料表清單中的介面。  如需存取來源檔案資訊的範例，請參閱[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)介面。  
  
```cpp#  
  
IDiaEnumSourceFiles* GetEnumSourceFiless(IDiaSession *pSession)  
{  
    IDiaEnumSourceFiles * pUnknown    = NULL;  
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);  
    IDiaEnumTables*       pEnumTables = NULL;  
    IDiaTable*            pTable      = NULL;  
    ULONG                 celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)