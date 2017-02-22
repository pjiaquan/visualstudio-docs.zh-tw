---
title: "IDiaInjectedSource::get_length | Microsoft Docs"
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
  - "IDiaInjectedSource::get_length 方法"
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的程式碼的位元組數目。  
  
## 語法  
  
```cpp#  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回程式碼的位元組數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 備註  
 這個方法所傳回的值的來源程式碼的長度，而且是相同的值，因為傳回的[IDiaInjectedSource::get\_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)方法。  
  
## 請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaInjectedSource::get\_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)