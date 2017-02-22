---
title: "IDiaInjectedSource::get_crc | Microsoft Docs"
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
  - "IDiaInjectedSource::get_crc 方法"
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource::get_crc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取從來源程式碼中的位元組計算的循環冗餘檢查 \(CRC\)。  
  
## 語法  
  
```cpp#  
HRESULT get_crc (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的 CRC 的計算方式從來源程式碼中的位元組。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)