---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
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
  - "IDiaDataSource::get_lastError 方法"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取上一次載入錯誤的檔案名稱。  
  
## 語法  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### 參數  
 pRetVal  
 \[\] out傳回字串，包含上次載入錯誤相關聯的.pdb 檔案名稱。  
  
## 傳回值  
 傳回由載入作業所造成的最後一個錯誤碼。  傳回`E_INVALIDARG`如果`pRetVal`參數是`NULL`。  
  
## 範例  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## 請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)