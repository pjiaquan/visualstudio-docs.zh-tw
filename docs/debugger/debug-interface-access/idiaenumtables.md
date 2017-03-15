---
title: "IDiaEnumTables | Microsoft Docs"
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
  - "IDiaEnumTables 介面"
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列舉各種資料來源中所包含的資料表。  
  
## 語法  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaEnumTables`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaEnumTables::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|擷取[IEnumVARIANT Interface](http://msdn.microsoft.com/zh-tw/139e3c93-faef-4003-9079-e0e94494db3e)版的這個列舉值。|  
|[IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|擷取資料表的數目。|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|擷取資料表的索引或名稱。|  
|[IDiaEnumTables::Next](../Topic/IDiaEnumTables::Next.md)|擷取指定的列舉型別序列中的資料表。|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|略過指定的數目的列舉型別序列中的資料表。|  
|[IDiaEnumTables::Reset](../Topic/IDiaEnumTables::Reset.md)|將列舉型別序列重設至開頭。|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
  
## 備註  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)方法。  
  
## 範例  
 本範例示範如何取得`IDiaEnumTables`與工作階段的介面。  使用資料表的更完整的範例，請參閱[IDiaTable](../../debugger/debug-interface-access/idiatable.md)介面。  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)