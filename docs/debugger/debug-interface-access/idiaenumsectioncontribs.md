---
title: "IDiaEnumSectionContribs | Microsoft Docs"
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
  - "IDiaEnumSectionContribs 介面"
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSectionContribs
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列舉各種資料來源中所含的區段貢獻。  
  
## 語法  
  
```  
IDiaEnumSectionContribs : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaEnumSectionContribs`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaEnumSectionContribs::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|擷取[IEnumVARIANT Interface](http://msdn.microsoft.com/zh-tw/139e3c93-faef-4003-9079-e0e94494db3e)版的這個列舉值。|  
|[IDiaEnumSectionContribs::get\_Count](../Topic/IDiaEnumSectionContribs::get_Count.md)|擷取數\] 區段的貢獻。|  
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|擷取的索引的區段佔的比重。|  
|[IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)|擷取指定的區段列舉序列中的比重。|  
|[IDiaEnumSectionContribs::Skip](../Topic/IDiaEnumSectionContribs::Skip.md)|略過指定的數目的列舉型別序列中的區段貢獻。|  
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|將列舉型別序列重設至開頭。|  
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
  
## 備註  
  
## 呼叫者的附註  
 取得這個介面，從[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)方法。  範例中的，如需詳細資訊，請參閱。  
  
## 範例  
 本範例示範如何取得 \( `GetEnumSectionContribs`函式\)，並使用 \( `ShowSectionContribs`函式\) `IDiaEnumSectionContribs`介面。  使用區段貢獻的更完整的範例，請參閱[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)介面。  
  
```cpp#  
  
      IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);  
    IDiaEnumTables*          pEnumTables = NULL;  
    IDiaTable*               pTable      = NULL;  
    ULONG                    celt        = 0;  
  
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
  
void ShowSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pEnumSectionContribs;  
  
    pEnumSectionContribs = GetEnumSectionContribs(pSession);  
    if (pSectionContrib != NULL)  
    {  
        IDiaSectionContrib* pSectionContrib;  
        ULONG celt = 0;  
  
        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintSectionContrib(pSectionContrib, pSession);  
            pSectionContrib->Release();  
        }  
        pSectionContrib->Release();   
    }  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)