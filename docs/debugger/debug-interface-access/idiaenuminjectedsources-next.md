---
title: "IDiaEnumInjectedSources::Next | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Next 方法"
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的列舉型別序列中的插入來源。  
  
## 語法  
  
```cpp#  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### 參數  
 celt  
 \[in\]要擷取列舉值中的插入來源的數目。  
  
 rgelt  
 \[\] out傳回陣列的[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) ，表示您想要插入的來源物件。  
  
 pceltFetched  
 \[\] out傳回已擷取的列舉值中的插入來源的數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`不會再插入的來源時。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)