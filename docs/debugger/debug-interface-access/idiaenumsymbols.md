---
title: "IDiaEnumSymbols | Microsoft Docs"
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
  - "IDiaEnumSymbols 介面"
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbols
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列舉各種資料來源中所包含的符號。  
  
## 語法  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaEnumSymbols`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaEnumSymbols::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|擷取`IEnumVARIANT Interface`版的這個列舉值。|  
|[IDiaEnumSymbols::get\_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|擷取符號的數目。|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|擷取的索引的符號。|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|擷取指定的列舉型別序列中的符號數目。|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|略過指定的數目的列舉型別序列中的符號。|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|將列舉型別序列重設至開頭。|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
  
## 備註  
 這個介面會提供透過特定類型的符號，例如，分組的符號`SymTagUDT` \(使用者定義的型別\) 或`SymTagBaseClass`。  若要使用位址來分組的符號，請使用[IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)介面。  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫下列方法：  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
-   [IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## 範例  
 本範例示範如何取得`IDiaEnumSymbols`介面，然後使用 \[清單使用者定義型別 \(Udt\) 該列舉型別。  
  
> [!NOTE]
>  `CDiaBSTR`是一個類別，會換行`BSTR` ，並自動處理具現化超出範圍時，請釋出的字串。  
  
```cpp#  
void ShowUDTs(IDiaSymbol *pGlobals)  
{  
    CComPtr<IDiaEnumSymbols> pEnum;  
    CComPtr<IDiaSymbol> pSymbol;  
    HRESULT hr;  
  
    hr = pGlobals->findChildren(SymTagUDT,  
                                NULL,  
                                nsfCaseInsensitive | nsfUndecoratedName,  
                                &pEnum);  
    if (hr == S_OK)  
    {  
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR name;  
            if ( pSymbol->get_name( &name ) != S_OK )  
                Fatal( "get_name" );  
            printf( "Found UDT: %ws\n", name );  
            pSymbol = 0;  
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
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)