---
title: "IDiaPropertyStorage::ReadLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadLONG"
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

讀取`LONG`屬性集合中的值。  
  
## 語法  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### 參數  
 `id`  
 \[in\]若要讀取之屬性識別項 \(`PROPID`與 WTypes.h 所述`ULONG`\)。  
  
 `pValue`  
 \[\] out傳回屬性值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  傳回`E_INVALIDARG`如果屬性不是型別的`LONG`。  
  
## 備註  
 A `LONG`由 Windows 為 32 位元帶正負號的整數所定義。  
  
## 請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)