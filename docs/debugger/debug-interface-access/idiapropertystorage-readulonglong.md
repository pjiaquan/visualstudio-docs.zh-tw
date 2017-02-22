---
title: "IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadULONGLONG"
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

讀取`ULONGLONG`屬性集合中的值。  
  
## 語法  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### 參數  
 `id`  
 \[in\]若要讀取之屬性識別項 \(`PROPID`與 WTypes.h 所述`ULONG`\)。  
  
 `pValue`  
 \[\] out傳回屬性值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  傳回`E_INVALIDARG`如果屬性不是型別的`ULONGLONG`。  
  
## 備註  
 A `ULONGLONG`由 Windows 為 64 位元不帶正負號的整數所定義。  
  
## 請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)