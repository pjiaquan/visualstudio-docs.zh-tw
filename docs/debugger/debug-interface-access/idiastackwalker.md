---
title: "IDiaStackWalker | Microsoft Docs"
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
  - "IDiaStackWalker 介面"
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

提供方法，以執行堆疊查核行程使用.pdb 檔案中的資訊。  
  
## 語法  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaStackWalker`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|擷取列舉堆疊框架值 x 86 的平台。|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|擷取特定的平台類型的堆疊框架列舉器。|  
  
## 備註  
 這個介面用來取得已載入的模組的堆疊框架的清單中。  每個方法會傳遞[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) \(由用戶端應用程式\) 的物件會提供所需的資訊建立堆疊框架的清單。  
  
## 呼叫者的備忘稿  
 這個介面藉由呼叫`CoCreateInstance`方法與類別識別項`CLSID_DiaStackWalker`的介面識別碼`IID_IDiaStackWalker`。  此範例顯示如何取得這個介面。  
  
## 範例  
 本範例示範如何取得`IDiaStackWalker`介面。  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)