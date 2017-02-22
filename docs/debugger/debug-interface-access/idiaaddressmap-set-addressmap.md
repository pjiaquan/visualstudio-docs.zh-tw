---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
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
  - "IDiaAddressMap::set_addressMap 方法"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

提供支援的影像配置轉譯的位址對應。  
  
## 語法  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### 參數  
 `cbData`  
 \[in\]中的項目數`data`參數。  
  
 `data[]`  
 \[in\]陣列的[DiaAddressMapEntry 結構](../../debugger/debug-interface-access/diaaddressmapentry.md)定義轉譯對應的結構。  
  
 `imagetoSymbols`  
 \[in\]`TRUE`如果`data`參數會定義新的影像配置地圖上原來的版面配置 \(如所述的偵錯符號\)。  `FALSE`如果`data`是取自原始配置的新影像配置對應。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 通常，DIA 會擷取位址轉譯對應程式資料庫 \(.pdb\) 檔案中。  如果這些值已遺失， [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)方法被呼叫兩次，一次是使用`imagetoSymbols`參數設為`TRUE` ，一次是使用`imagetoSymbols`參數設為`FALSE`。  無法啟用位址對應轉譯，使用[IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md)方法，因此除非這兩種轉譯對應所提供。  
  
## 請參閱  
 [DiaAddressMapEntry 結構](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)