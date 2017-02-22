---
title: "IDiaSegment | Microsoft Docs"
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
  - "IDiaSegment 介面"
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSegment
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

將對應的位址空間的區段將章節編號的資料。  
  
## 語法  
  
```  
IDiaSegment : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaSegment`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaSegment::get\_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|擷取區段編號。|  
|[IDiaSegment::get\_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|擷取一節的起始處的區段中的位移。|  
|[IDiaSegment::get\_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|擷取區段中的位元組的數目。|  
|[IDiaSegment::get\_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|會擷取旗標，指出是否可讀取該區段。|  
|[IDiaSegment::get\_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|會擷取旗標，指出是否可以修改該區段。|  
|[IDiaSegment::get\_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|會擷取旗標，指出是否可執行檔的區段。|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|擷取對應至這個區段的區段數目。|  
|[IDiaSegment::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|擷取區段開頭的相對虛擬的位址 \(RVA\)。|  
|[IDiaSegment::get\_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|擷取區段開頭的虛擬位址 \(VA\)。|  
  
## 備註  
 因為 DIA SDK 已經從區段位移，轉譯執行相對虛擬位址，不會讓大部分的應用程式使用的對應區段中的資訊。  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫[IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)或[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)方法。  範例中的，如需詳細資訊，請參閱。  
  
## 範例  
 這個函式會顯示所有的區段的位址中的資料表和最接近的符號。  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
            }  
        }  
    }  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)