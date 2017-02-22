---
title: "IDiaSectionContrib::get_virtualAddress | Microsoft Docs"
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
  - "IDiaSectionContrib::get_virtualAddress 方法"
ms.assetid: e5b44a81-0804-429b-97d8-467cbba3132a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_virtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取所佔比重的虛擬位址 \(VA\)。  
  
## 語法  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回所佔比重的 VA。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)