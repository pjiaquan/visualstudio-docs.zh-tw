---
title: "IDiaEnumDebugStreams::get_Count | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::get_Count 方法"
ms.assetid: 5c13fa9a-b35e-47b0-806f-1f53bfe1ba89
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams::get_Count
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取偵錯資料流數目。  
  
## 語法  
  
```cpp#  
HRESULT get_Count(   
   LONG* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回這個列舉值中可用的偵錯資料流數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)