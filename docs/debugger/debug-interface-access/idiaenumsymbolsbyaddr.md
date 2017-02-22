---
title: "IDiaEnumSymbolsByAddr | Microsoft Docs"
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
  - "IDiaEnumSymbolsbyAddr 介面"
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列舉各種資料來源中所包含的符號的位址。  
  
## 語法  
  
```  
IDiaEnumSymbolsByAddr : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaEnumSymbolsByAddr`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|藉由執行對應的區段\] 與 \[位移位置的列舉值。|  
|[IDiaEnumSymbolsByAddr::symbolByRVA](../Topic/IDiaEnumSymbolsByAddr::symbolByRVA.md)|定位列舉值的相對虛擬位址 \(RVA\) 執行查詢。|  
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|藉由執行對應的虛擬位址 \(VA\) 中放置列舉值。|  
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|位址所擷取的順序的下一個符號。  更新列舉值位置擷取的項目數目。|  
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|藉由前一個符號的順序來擷取位址。  更新列舉值位置擷取的項目數目。|  
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|製作物件的複本。|  
  
## 備註  
 這個介面會提供地址來分組的符號。  若要使用符號按類型分組，例如`SymTagUDT` \(使用者定義型別\) 或`SymTagBaseClass`，使用[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)介面。  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)方法。  
  
## 範例  
 這個函式會顯示排序的相對虛擬位址的所有符號的位址與名稱。  
  
```cpp#  
void ShowSymbolsByAddress(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;  
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )  
    {  
        Fatal( "getSymbolsByAddr" );  
    }  
    CComPtr<IDiaSymbol> pSym;  
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )  
    {  
        Fatal( "symbolByAddr" );  
    }  
    DWORD rvaLast = 0;  
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )  
    {  
        pSym = 0;  
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )  
        {  
            Fatal( "symbolByAddr" );  
        }  
        printf( "Symbols in order\n" );  
        do  
        {   
            CDiaBSTR name;  
            if ( pSym->get_name( &name ) != S_OK )  
            {  
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );  
            }  
            else  
            {  
               printf( "\t0x%08X %ws\n", rvaLast, name );  
            }  
            pSym = 0;  
            celt = 0;  
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )  
            {  
                break;  
            }  
        } while ( celt == 1 );  
    }  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)