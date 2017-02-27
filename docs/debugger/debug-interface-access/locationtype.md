---
title: "LocationType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LocationType 列舉"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

表示包含在符號中的位置資訊種類。  
  
## 語法  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## 項目  
 `LocIsNull`  
 沒有可用的位置資訊。  
  
 `LocIsStatic`  
 位置是靜態的。  
  
 `LocIsTLS`  
 位置是在執行緒區域儲存區中。  
  
 `LocIsRegRel`  
 位置是暫存器的相對位置。  
  
 `LocIsThisRel`  
 一定是位於`this`\-相對。  
  
 `LocIsEnregistered`  
 位置是在暫存器。  
  
 `LocIsBitField`  
 位置是位元欄位。  
  
 `LocIsSlot`  
 位置是 Microsoft 中繼語言 \(MSIL\) 介面槽。  
  
 `LocIsIlRel`  
 位置是相對於 MSIL。  
  
 `LocInMetaData`  
 位置是在中繼資料中。  
  
 `LocIsConstant`  
 位置是常數值。  
  
 `LocTypeMax`  
 這個列舉型別中的位置型別數目。  
  
## 備註  
 可用的屬性來[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)介面的影像檔中符號的位置而定。  如需詳細資訊，請參閱 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)。  
  
 這個列舉型別中的值會傳回由呼叫[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)方法。  
  
## 需求  
 標頭: cvconst.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)