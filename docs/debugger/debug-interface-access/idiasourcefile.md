---
title: "IDiaSourceFile | Microsoft Docs"
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
  - "IDiaSourceFile 介面"
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

代表原始程式檔。  
  
## 語法  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaSourceFile`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaSourceFile::get\_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|擷取對這個影像是唯一的一個簡單的整數值。|  
|[IDiaSourceFile::get\_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|擷取原始程式檔名稱。|  
|[IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|擷取加總檢查碼型別。|  
|[IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|與參考此檔案的行號會擷取列舉值的編譯。|  
|[IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|擷取的加總檢查碼位元組。|  
  
## 備註  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)或[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)方法。  範例中的，如需詳細資訊，請參閱。  
  
## 範例  
 這個函式會顯示所有的原始程式檔，做為指定的資料表的名稱。  
  
```cpp#  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
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
 [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [IDiaLineNumber::get\_sourceFile](../Topic/IDiaLineNumber::get_sourceFile.md)   
 [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)