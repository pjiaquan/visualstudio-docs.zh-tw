---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
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
  - "IDiaDataSource::loadAndValidateDataFromPdb 方法"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會開啟，並驗證程式資料庫 \(.pdb\) 檔案符合簽章提供的資訊，並準備.pdb 檔做為偵錯資料來源。  
  
## 語法  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### 參數  
 `pdbPath`  
 \[in\].pdb 檔的路徑。  
  
 `pcsig70`  
 \[in\]GUID 簽章以供驗證的.pdb 檔案簽章。  只有.pdb 檔案的[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] ，稍後有 GUID 簽章。  
  
 `sig`  
 \[in\]32 位元簽章以供驗證的.pdb 檔案簽章。  
  
 `age`  
 \[in\]若要確認有效期的值。  年齡不一定對應到任何已知的時間值，它用來判斷這是否為與相對應的.exe 檔案不同步的.pdb 檔。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  下表顯示可能的傳回值，這個方法。  
  
|值|描述|  
|-------|--------|  
|E\_PDB\_NOT\_FOUND|無法開啟檔案，或檔案格式無效。|  
|E\_PDB\_FORMAT|嘗試存取的檔案格式太舊。|  
|E\_PDB\_INVALID\_SIG|簽章不符。|  
|E\_PDB\_INVALID\_AGE|時代不符。|  
|E\_INVALIDARG|不正確的參數。|  
|E\_UNEXPECTED|已完成資料來源。|  
  
## 備註  
 .Pdb 檔案包含簽章\] 和 \[年齡\] 值。  這些值會複寫中的.exe 或.dll 檔案符合.pdb 檔。  準備資料來源，這個方法會驗證已命名的.pdb 檔案的簽章和年齡符合提供的值。  
  
 若要載入而不需驗證的.pdb 檔案，請使用[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)方法。  
  
 若要存取資料載入程序 \(透過回呼機制\)，請使用[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
 若要直接從記憶體載入.pdb 檔，請使用[IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)方法。  
  
## 範例  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## 請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)