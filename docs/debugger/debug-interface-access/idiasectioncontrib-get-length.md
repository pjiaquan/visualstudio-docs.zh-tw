---
title: "IDiaSectionContrib::get_length | Microsoft Docs"
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
  - "IDiaSectionContrib::get_length 方法"
ms.assetid: d0f6b9c7-90fc-4e3c-945a-b8f683a8f006
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取一節中的位元組的數目。  
  
## 語法  
  
```cpp#  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回某一節的位元組數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)