---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
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
  - "IDiaDataSource::loadDataForExe 方法"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會開啟並做準備.exe\/.dll 檔案相關聯的偵錯資料。  
  
## 語法  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### 參數  
 executable  
 \[in\].Exe 或.dll 的檔案路徑。  
  
 searchPath  
 \[in\]若要搜尋偵錯資料的替代路徑。  
  
 pCallback  
 \[in\]`IUnknown`介面之物件的支援偵錯回呼介面，例如[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)， [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)、 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)，和 \(或\) [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)介面。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  下表顯示一些可能的錯誤代碼，這個方法。  
  
|值|描述|  
|-------|--------|  
|E\_PDB\_NOT\_FOUND|無法開啟檔案，或檔案格式無效。|  
|E\_PDB\_FORMAT|嘗試存取的檔案格式太舊。|  
|E\_PDB\_INVALID\_SIG|簽章不符。|  
|E\_PDB\_INVALID\_AGE|時代不符。|  
|E\_INVALIDARG|不正確的參數。|  
|E\_UNEXPECTED|已完成資料來源。|  
  
## 備註  
 偵錯.exe\/.dll 檔案標頭名稱相關的偵錯資料的位置。  
  
 這個方法會偵錯標頭，然後搜尋並準備偵錯資料。  搜尋的進度，\(選擇性\) 可以報告和回呼朋友和家人。  例如， [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)時叫用`IDiaDataSource::loadDataForExe`方法會尋找並處理偵錯目錄。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)和[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)介面讓用戶端應用程式提供的可執行檔中讀取資料，無法直接透過標準的檔案 I\/O 存取檔案時的替代方法。  
  
 若要載入而不需驗證的.pdb 檔案，請使用[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)方法。  
  
 若要驗證.pdb 檔案是否符合特定準則，請使用[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)方法。  
  
 若要直接從記憶體載入.pdb 檔，請使用[IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)方法。  
  
## 範例  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## 請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)