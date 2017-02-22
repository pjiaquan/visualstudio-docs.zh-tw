---
title: "DiaAddressMapEntry | Microsoft Docs"
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
  - "DiaAddressMapEntry 列舉"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

說明中的地址對應的項目。  
  
## 語法  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## 項目  
 `rva`  
 答： 影像中相對虛擬位址 \(RVA\)  
  
 `rvaTo`  
 相對虛擬位址`rva`會對應到在映像 b。  
  
## 備註  
 將位址對應提供譯自一個映像的版面配置 \(A\) 到另一個 \(B\)。  陣列的`DiaAddressMapEntry`結構按照`rva`定義地址對應。  
  
 若要翻譯一個位址， `addrA`，到地址的映像 a 中`addrB`，b 的影像，請執行下列步驟：  
  
1.  搜尋的對應項目， `e`，具有最大`rva`小於或等於`addrA`。  
  
2.  Set `delta = addrA – e.rva`.  
  
3.  Set `addrB = e.rvaTo + delta`.  
  
 陣列的`DiaAddressMapEntry`結構傳遞至[IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。  
  
## 需求  
 標頭: dia2.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)