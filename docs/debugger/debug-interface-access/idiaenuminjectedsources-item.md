---
title: "IDiaEnumInjectedSources::Item | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Item 方法"
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumInjectedSources::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會插入的來源擷取的索引。  
  
## 語法  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### 參數  
 Index \- 索引  
 \[in\]索引的[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)要擷取的物件。  索引是以介於 0 到`count`\-1，其中`count`傳回的[IDiaEnumInjectedSources::get\_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)方法。  
  
 injectedSource  
 \[\] out傳回[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)物件，代表插入的來源。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)