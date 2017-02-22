---
title: "IDiaSectionContrib::get_addressOffset | Microsoft Docs"
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
  - "IDiaSectionContrib::get_addressOffset 方法"
ms.assetid: 4d569323-0e11-456d-9f92-a218bf292ecf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_addressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取位移所佔比重的地址部份。  
  
## 語法  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回位移所佔比重的地址部份。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)