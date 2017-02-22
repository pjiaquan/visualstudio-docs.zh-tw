---
title: "IDiaDataSource::openSession | Microsoft Docs"
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
  - "IDiaDataSource::openSession 方法"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

開啟查詢符號的工作階段。  
  
## 語法  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### 參數  
 ppSession  
 \[\] out傳回[IDiaSession](../../debugger/debug-interface-access/idiasession.md)物件，表示開啟的工作階段。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  下表顯示可能的傳回值，這個方法。  
  
|值|描述|  
|-------|--------|  
|E\_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)物件先前尚未初始化符號的來源。|  
|E\_INVALIDARG|無效`ppSession`參數。|  
|E\_OUTOFMEMORY|記憶體不足，無法開啟工作階段。|  
  
## 備註  
 這個方法會開啟[IDiaSession](../../debugger/debug-interface-access/idiasession.md)為資料來源的物件。  
  
 `IDiaSession`物件會實作查詢到資料來源。  工作階段管理一個地址空間，以讓每一組的偵錯符號。  由資料來源的符號所描述的.exe 或.dll 檔案是否作用中，在多個位址範圍 \(例如，因為多個處理序已載入它\)，然後適用於每個位址範圍的一個工作階段\]。  
  
## 範例  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## 請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)