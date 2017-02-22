---
title: "IDiaEnumSymbols::get_Count | Microsoft Docs"
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
  - "IDiaEnumSymbols::get_Count 方法"
ms.assetid: fdaae6d7-e67b-4262-84c9-fbae381e8297
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbols::get_Count
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取符號的數目。  
  
## 語法  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### 參數  
 pRetVal  
 \[\] out傳回符號的數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)