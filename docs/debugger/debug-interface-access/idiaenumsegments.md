---
title: "IDiaEnumSegments | Microsoft Docs"
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
  - "IDiaEnumSegments 介面"
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列舉各種資料來源中所含的區段。  
  
## 語法  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaEnumSegments`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaEnumSegments::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|擷取[IEnumVARIANT Interface](http://msdn.microsoft.com/zh-tw/139e3c93-faef-4003-9079-e0e94494db3e)版的這個列舉值。|  
|[IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|擷取的線段數目。|  
|[IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)|擷取的索引的區段。|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|擷取指定的列舉型別序列中的區段數目。|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|略過指定的列舉型別序列的線段數目。|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|將列舉型別序列重設至開頭。|  
|[IDiaEnumSegments::Clone](../Topic/IDiaEnumSegments::Clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
  
## 備註  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫`QueryInterface`上的方法[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件。  範例中的，如需詳細資訊，請參閱。  
  
## 範例  
 本範例示範如何取得`IDiaEnumSections`資料表中的介面。  使用區段的更完整的範例，請參閱[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)介面。  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)