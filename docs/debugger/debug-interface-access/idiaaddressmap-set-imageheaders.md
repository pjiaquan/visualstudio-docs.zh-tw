---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
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
  - "IDiaAddressMap::set_imageHeaders 方法"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定影像標頭來啟用相對虛擬位址轉譯。  
  
## 語法  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### 參數  
 cbData  
 \[in\]標頭資料的位元組數目。  必須是`n*sizeof(IMAGE_SECTION_HEADER)` ， `n`是可執行檔中區段標頭數目。  
  
 資料\]  
 \[in\]陣列的`IMAGE_SECTION_HEADER`結構，以做為影像標頭。  
  
 originalHeaders  
 \[in\]設定為 `FALSE`的映像標頭時從新的映像， `TRUE`如果它們反映於升級原始的影像。  一般而言，這會設定為`TRUE`只能在與呼叫一起[IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 `IMAGE_SECTION_HEADER`結構 Winnt.h 中宣告，並代表影像區段標頭格式的可執行檔。  
  
 相對虛擬位址計算取決於`IMAGE_SECTION_HEADER`的值。  通常，DIA 會擷取這些程式資料庫 \(.pdb\) 檔案中。  如果缺少這些值，是無法計算相對虛擬位址的 DIA 和[IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)方法傳回`FALSE`。  用戶端必須再呼叫[IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)方法，以提供從映像本身遺漏的映像標頭後啟用相對虛擬位址計算。  
  
## 請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)