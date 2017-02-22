---
title: "IDiaPropertyStorage::ReadDWORD | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadDWORD"
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

讀取`DWORD`屬性集合中的值。  
  
## 語法  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### 參數  
 `id`  
 \[in\]若要讀取之屬性識別項 \(`PROPID`與 WTypes.h 所述`ULONG`\)。  
  
 `pValue`  
 \[\] out傳回屬性值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  傳回`E_INVALIDARG`如果屬性不是型別的`DWORD`。  
  
## 備註  
 A `DWORD` Windows 所定義的 32 位元不帶正負號之整數形式。  
  
## 請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)