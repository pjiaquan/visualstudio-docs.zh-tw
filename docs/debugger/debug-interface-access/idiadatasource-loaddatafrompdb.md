---
title: "IDiaDataSource::loadDataFromPdb | Microsoft Docs"
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
  - "IDiaDataSource::loadDataFromPdb 方法"
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會開啟並做準備的程式資料庫 \(.pdb\) 檔案做為偵錯資料來源。  
  
## 語法  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### 參數  
 pdbPath  
 \[in\].pdb 檔的路徑。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  下表顯示可能的傳回值，這個方法。  
  
|值|描述|  
|-------|--------|  
|E\_PDB\_NOT\_FOUND|無法開啟檔案，或決定此檔案包含無效的格式。|  
|E\_PDB\_FORMAT|嘗試存取的檔案格式太舊。|  
|E\_INVALIDARG|不正確的參數。|  
|E\_UNEXPECTED|已完成資料來源。|  
  
## 備註  
 這個方法會載入偵錯資料，直接從.pdb 檔案。  
  
 若要驗證.pdb 檔案是否符合特定準則，請使用[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)方法。  
  
 若要存取資料載入程序 \(透過回呼機制\)，請使用[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
 若要直接從記憶體載入.pdb 檔，請使用[IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)方法。  
  
## 範例  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## 請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)