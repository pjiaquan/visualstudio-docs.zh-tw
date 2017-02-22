---
title: "IDiaInjectedSource | Microsoft Docs"
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
  - "IDiaInjectedSource 介面"
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

存取插入儲存在 DIA 的資料來源中的原始程式碼。  
  
## 語法  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaInjectedSource`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaInjectedSource::get\_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|擷取從來源程式碼中的位元組計算的循環冗餘檢查 \(CRC\)。|  
|[IDiaInjectedSource::get\_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|擷取的程式碼的位元組數目。|  
|[IDiaInjectedSource::get\_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|擷取來源的檔案名稱。|  
|[IDiaInjectedSource::get\_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|擷取原始檔所編譯的目的檔名稱。|  
|[IDiaInjectedSource::get\_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|擷取指定給非檔案來源的程式碼路徑。 也就是插入的程式碼。|  
|[IDiaInjectedSource::get\_sourceCompression](../Topic/IDiaInjectedSource::get_sourceCompression.md)|擷取來源使用的壓縮的指示器。|  
|[IDiaInjectedSource::get\_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|擷取來源的程式碼位元組。|  
  
## 備註  
 插入的來源是在編譯期間會插入的文字。  這不表示前置處理器`#include` C\+\+ 中使用。  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)或[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)方法。  請參閱[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)介面取得的例如`IDiaInjectedSource`介面。  
  
## 範例  
 本範例將顯示的資料可以從`IDiaInjectedSource`介面。  另一種方法使用的[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)介面，請參閱範例[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)介面。  
  
```cpp#  
void PrintInjectedSource(IDiaInjectedSource* pSource)  
{  
    ULONGLONG codeLength      = 0;  
    DWORD     crc             = 0;  
    DWORD     compressionType = 0;  
    BSTR      sourceFilename  = NULL;  
    BSTR      objectFilename  = NULL;  
    BSTR      virtualFilename = NULL;  
  
    std::cout << "Injected Source:" << std::endl;  
    if (pSource != NULL)  
    {  
        if (pSource->get_crc(&crc) == S_OK &&  
            pSource->get_sourceCompression(&compressionType) == S_OK &&  
            pSource->get_length(&codeLength) == S_OK)  
        {  
            wprintf(L"  crc = %lu\n", crc);  
            wprintf(L"  code length = %I64u\n",codeLength);  
            wprintf(L"  compression type code = %lu\n", compressionType);  
        }  
  
        wprintf(L"  source filename: ");  
        if (pSource->get_filename(&sourceFilename) == S_OK)  
        {  
            wprintf(L"%s", sourceFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  object filename: ");  
        if (pSource->get_filename(&objectFilename) == S_OK)  
        {  
            wprintf(L"%s", objectFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  virtual filename: ");  
        if (pSource->get_filename(&virtualFilename) == S_OK)  
        {  
            wprintf(L"%s", virtualFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        SysFreeString(sourceFilename);  
        SysFreeString(objectFilename);  
        SysFreeString(virtualFilename);  
    }  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)