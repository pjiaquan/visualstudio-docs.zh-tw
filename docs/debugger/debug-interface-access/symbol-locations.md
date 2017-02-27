---
title: "符號位置 | Microsoft Docs"
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
  - "LocationType 值"
  - "符號 [DIA SDK], 位置"
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 符號位置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

大部分的符號已定義的位置的影像檔中。  符號的位置指定其值介於[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)列舉型別。  該符號可能支援其他的屬性，它的位置而定。  
  
 下表顯示最常使用的位置型別和其額外的屬性。  
  
|位置類型|其他屬性|  
|----------|----------|  
|`LocIsNull`|無|  
|`LocIsStatic`|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)\(如果您啟用相對虛擬位址\)<br /><br /> [IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)\(如果映像基底已設定為非零值\)|  
|`LocIsTLS`|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get\_registerId](../Topic/IDiaSymbol::get_registerId.md)<br /><br /> [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get\_registerId](../Topic/IDiaSymbol::get_registerId.md)|  
|`LocIsBitField`|[IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## 請參閱  
 [IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)   
 [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [IDiaSymbol::get\_registerId](../Topic/IDiaSymbol::get_registerId.md)   
 [IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)