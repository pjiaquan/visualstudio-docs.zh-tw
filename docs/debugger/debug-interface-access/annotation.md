---
title: "註釋 | Microsoft Docs"
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
  - "SymTabAnnotation 符號"
  - "註釋符號"
ms.assetid: eb9f759b-98a5-45fc-b085-91f1f2666e72
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 註釋
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

位置的程式碼可以使用加註`SymTagAnnotation`符號。  
  
## 屬性  
 下表會對此符號的型別有效的屬性。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|位移的組件的位置。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|區段的組件的位置。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|其中一個 [DataKind 列舉](../../debugger/debug-interface-access/datakind.md) 值。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此附註在它的模組中的相對位置。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagAnnotation` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|常數的資料值。|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|這個可執行檔映像中的註解的位置。|  
  
## 請參閱  
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)