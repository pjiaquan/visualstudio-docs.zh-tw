---
title: "IDiaAddressMap::get_relativeVirtualAddressEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::get_relativeVirtualAddressEnabled 方法"
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::get_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指出是否啟用的計算和相對虛擬位址 \(RVA\) 的使用。  
  
## 語法  
  
```cpp#  
HRESULT get_relativeVirtualAddressEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 pRetVal  
 \[\] out傳回`TRUE`如果已啟用之 Rva 計算。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 如果區段有一開始載入 PDB 檔中，會啟用 Rva。  Rva 的使用可以暫時停用藉由呼叫[IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)方法。  
  
 此外，建立新的映像標頭，藉由呼叫[IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)方法後面接著呼叫`put_relativeVirtualAddressEnabled`若要在使用新的映像標頭的 Rva 的使用方法。  
  
## 請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)