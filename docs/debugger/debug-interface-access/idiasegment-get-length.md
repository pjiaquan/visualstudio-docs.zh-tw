---
title: "IDiaSegment::get_length | Microsoft Docs"
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
  - "IDiaSegment::get_length 方法"
ms.assetid: 5d92e394-649b-49f2-bce7-12dd9d666d85
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSegment::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取區段中的位元組的數目。  
  
## 語法  
  
```cpp#  
HRESULT get_ length (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out區段中傳回位元組的數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)