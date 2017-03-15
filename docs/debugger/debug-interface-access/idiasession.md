---
title: "IDiaSession | Microsoft Docs"
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
  - "IDiaSession 介面"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

提供查詢內容為偵錯符號。  
  
## 語法  
  
```  
IDiaSession : IUnknown  
```  
  
## 方法  
 下表顯示 `IDiaSession`方法。  
  
|方法|描述|  
|--------|--------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|擷取對應於符號在這個符號存放區的可執行檔的載入位址。  這是傳遞給 `put_loadAddress` 方法中相同的值。|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|設定對應至符號在這個符號存放區的可執行檔的載入位址。 **Note:**  呼叫這個方法非常重要，當您取得 `IDiaSession` 物件，此時，就能開始使用物件之前。|  
|[IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)|擷取在全域範圍的參考。|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|擷取在符號存放區中的所有資料表的列舉值。|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|在靜態位置擷取所有具名符號的列舉值。|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|擷取符合名稱和符號類型指定的父、識別項的所有子系。|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|擷取包含所指定數目的符號型別，或者是最接近時，指定的電子郵件地址。|  
|[IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)|擷取包含所指定數目的符號型別，或者是最接近時，指定的相對虛擬位址 \(RVA\) \(RVA\)。|  
|[IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)|擷取包含所指定數目的符號型別，或者是最接近時，指定的相對虛擬位址 \(RVA\) \(VA\)。|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|擷取包含指定的中繼資料語彙基元的符號。|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|檢查兩個符號是否相等。|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|根據唯一識別項擷取符號。|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|擷取包含所指定數目的符號型別，或者是最接近時，指定的相對虛擬位址和位移。|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|擷取包含所指定數目的符號型別，或者是最接近時，指定的虛擬位址和位移。|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|以編譯和名稱擷取原始程式檔。|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|由原始程式檔識別項擷取原始程式檔。|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|擷取在指定的編譯和原始程式檔識別項內的行號。|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|擷取包含指定的位址會在指定的編譯的程式碼行。|  
|[IDiaSession::findLinesByRVA](../Topic/IDiaSession::findLinesByRVA.md)|擷取包含指定的相對虛擬位址所指定的編譯的程式碼行。|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|尋找在指定的位址範圍包含行的行號資訊。|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|由原始程式檔和行號擷取指定的編譯的程式碼行。|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|擷取已放入符號存放區由屬性提供者或編譯程序的其他元件的來源。|  
|[IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)|若要擷取列舉型別序列的偵錯資料流。|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|擷取可讓用戶端透過所有在指定位址的內嵌框架逐一查看的列舉值。|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|擷取可讓用戶端透過所有在指定的相對虛擬位址\(RVA\) \(RVA\)內嵌框架逐一查看的列舉值。|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|擷取可讓用戶端透過所有在指定的相對虛擬位址\(RVA\) \(VA\)內嵌框架逐一查看的列舉值。|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|擷取可讓用戶端透過指定的行號資訊重複內嵌，直接或間接，根據指定的父代符號的列舉型別。|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|擷取可讓用戶端透過指定的行號資訊逐一查看由指定之父代符號內嵌，直接或間接，以及在指定的位址範圍內的列舉型別。|  
|[IDiaSession::findInlineeLinesByRVA](../Topic/IDiaSession::findInlineeLinesByRVA.md)|擷取可讓用戶端透過指定的行號資訊逐一查看由指定之父代符號內嵌，直接或間接，以及在指定的相對虛擬位址 \(RVA\) \(RVA\) 中的列舉型別。|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|擷取可讓用戶端透過指定的行號資訊逐一查看由指定之父代符號內嵌，直接或間接，以及在指定的相對虛擬位址 \(RVA\) \(VA\) 中的列舉型別。|  
|[IDiaSession::findInlineeLinesByLinenum](../Topic/IDiaSession::findInlineeLinesByLinenum.md)|擷取可讓用戶端透過指定的行號資訊會逐一查看指定的原始程式檔和行號內嵌，直接或間接，的列舉型別。|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|擷取可讓用戶端透過所有內嵌 \(Inline\) 函式行號資訊重複符合指定名稱的列舉型別。|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|傳回符號的列舉型別變數的指定標記值對應父快速 Stub 函式。|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|將對應的標記值，這個方法會傳回在指定的相對虛擬位址的指定父快速 Stub 函式包含符號的列舉型別。|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|傳回符號的列舉型別內嵌框架的與指定的內嵌函式名稱對應。|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|傳回符號的列舉型別對應至指定之來源位置的內嵌的框架。|  
  
## 備註  
 在建立物件之後 `IDiaSession` —和值傳遞至 `put_loadAddress` 方法必須是非零—符號所有虛擬位址 \(VA\) 屬性的是呼叫 [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) 方法很重要的存取。  載入位址來自任何程式載入偵錯的可執行檔。  例如，可以呼叫 Win32 函式 `GetModuleInformation` 擷取可執行的載入位址將控制代碼可執行檔。  
  
## 範例  
 做為 DIA SDK 的一般初始化的一部分，這個範例顯示如何取得 `IDiaSession` 介面。  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## 需求  
 標題:Dia2.h  
  
 程式庫:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)