---
title: "IDiaSectionContrib | Microsoft Docs"
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
  - "IDiaSectionContrib 介面"
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

描述區段中所佔比重的擷取資料，也就是連續的記憶體區塊至映像所產生的編譯。  
  
## 語法  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaSectionContrib`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaSectionContrib::get\_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|擷取提供本章節的編譯符號的參考。|  
|[IDiaSectionContrib::get\_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|擷取所佔比重的地址\] 區段部份。|  
|[IDiaSectionContrib::get\_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|擷取位移所佔比重的地址部份。|  
|[IDiaSectionContrib::get\_relativeVirtualAddress](../Topic/IDiaSectionContrib::get_relativeVirtualAddress.md)|擷取的映像相對虛擬位址 \(RVA\) 的比重。|  
|[IDiaSectionContrib::get\_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|擷取所佔比重的虛擬位址 \(VA\)。|  
|[IDiaSectionContrib::get\_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|擷取一節中的位元組的數目。|  
|[IDiaSectionContrib::get\_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|會擷取旗標，指出是否區段無法分頁記憶體用完。|  
|[IDiaSectionContrib::get\_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|會擷取旗標，表示是否區段應該不會填補接下來的記憶體界限。|  
|[IDiaSectionContrib::get\_code](../Topic/IDiaSectionContrib::get_code.md)|會擷取旗標，指出是否區段包含可執行程式碼。|  
|[IDiaSectionContrib::get\_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|會擷取旗標，指出是否區段包含 16 位元的程式碼。|  
|[IDiaSectionContrib::get\_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|會擷取旗標，指出是否區段包含初始化的資料。|  
|[IDiaSectionContrib::get\_uninitializedData](../Topic/IDiaSectionContrib::get_uninitializedData.md)|會擷取旗標，指出是否區段包含未初始化的資料。|  
|[IDiaSectionContrib::get\_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|會擷取旗標，指出是否一個區段包含註解或類似的資訊。|  
|[IDiaSectionContrib::get\_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|會擷取旗標，表示它由記憶體中影像的一部份之前，是否要移除區段。|  
|[IDiaSectionContrib::get\_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|會擷取旗標，指示區段是否為衝突的記錄。|  
|[IDiaSectionContrib::get\_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|會擷取旗標，指出是否可以捨棄一節。|  
|[IDiaSectionContrib::get\_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|會擷取旗標，指出是否無法快取的區段。|  
|[IDiaSectionContrib::get\_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|會擷取旗標，指出是否可以在記憶體中共用區段。|  
|[IDiaSectionContrib::get\_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|會擷取旗標，指出是否可執行程式碼區段。|  
|[IDiaSectionContrib::get\_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|會擷取旗標，指出是否可讀取的區段。|  
|[IDiaSectionContrib::get\_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|會擷取旗標，指出是否可寫入區段。|  
|[IDiaSectionContrib::get\_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|擷取的資料區段中的循環冗餘檢查 \(CRC\)。|  
|[IDiaSectionContrib::get\_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|擷取的 CRC 時的區段的重新配置資訊。|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|擷取一節的編譯時識別項。|  
  
## 備註  
  
## 呼叫者的備忘稿  
 這個介面藉由呼叫[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)和[IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)方法。  請參閱[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)介面取得的例如`IDiaSectionContrib`介面。  
  
## 範例  
 這個函式會顯示每個區段，以及任何相關符號的位址。  請參閱[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)介面，請參閱如何`IDiaSectionContrib`介面會取得。  
  
```cpp#  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
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
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)