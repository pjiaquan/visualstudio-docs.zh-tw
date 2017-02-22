---
title: "IDiaReadExeAtRVACallback | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback 介面"
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

可讓用戶端應用程式，提供可執行檔所指定的相對虛擬位址的位元組。  
  
## 語法  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaReadExeAtRVACallback`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|讀取指定的起始於指定的相對虛擬位址 \(RVA\) 可執行檔中的位元組數。|  
  
## 備註  
 用戶端應用程式會實作這個介面，以提供可執行檔使用到的可執行檔的相對虛擬位址的位元組。  若要使用絕對檔案位移，實作[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)介面。  
  
## 呼叫者的備忘稿  
 這個方法是由用戶端應用程式，而且傳遞給[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)做為替代的方法，讀取檔案的方法。  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)