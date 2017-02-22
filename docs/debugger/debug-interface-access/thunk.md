---
title: "Thunk | Microsoft Docs"
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
  - "Thunk 屬性 [DIA SDK]"
  - "Thunk 符號"
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Thunk
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

每個`thunk`由`SymTagThunk`標記。  
  
## 屬性  
 下表會對此符號的型別有效的屬性。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|存取修飾詞屬性，其中[CV\_access\_e 列舉](../../debugger/debug-interface-access/cv-access-e.md) \(僅在 DIA SDK V8.0 或更新版本\) 的值。|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|位移的組件的位置。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|區段的組件的位置。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|封入類別父系，如果有的話 \(只能在 DIA SDK V8.0 或更新\)。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|封入類別父系符號 \(只有在 DIA SDK V8.0 或更新版本\) 的 ID。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|如果這個 thunk 標示為 \[\(只有在 DIA SDK V8.0 或更新版本\) 的常數，則為 TRUE。|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|如果這個 thunk 是虛擬函式 \(僅在 DIA SDK V8.0 或更新版本\) 的簡介，則為 TRUE。|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|此 thunk 會被視為靜態 \(只有在 DIA SDK V8.0 或更新版本\)，其值為 TRUE。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|在這個 thunk 程式碼的位元組數目。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入編譯、 區塊或函式的符號。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|結束點具有靜態檔案的一部份。 如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)列舉型別。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|此 thunk 的名稱。|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|此 thunk 是純虛擬 \(只有在 DIA SDK V8.0 或更新版本\)，其值為 TRUE。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此 thunk，它的模組內的相對位置。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagThunk` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|這個範例的 thunk 目標位置的一部分。|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../Topic/IDiaSymbol::get_targetRelativeVirtualAddress.md)|`DWORD`|相對虛擬位址的 thunk 目標，其封閉區塊中。|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|區段的一部份 thunk 目標。|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|可執行檔映像中的 thunk 目標位置。|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Thunk 所定義的型別， [THUNK\_ORDINAL 列舉](../../debugger/debug-interface-access/thunk-ordinal.md)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|此 thunk \(只有在 DIA SDK V8.0 或更新版本\) 的型別。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|\(只有在 DIA SDK V8.0 或更新版本\) 的型別符號的識別碼。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`如果這個 thunk 未對齊 \(僅在 DIA SDK V8.0 或更新版本\)，|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE`如果這個 thunk 虛擬 \(只有在 DIA SDK V8.0 或更新\)。|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|此 thunk 可執行檔映像中的位置。|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|此 thunk \(只有在 DIA SDK V8.0 或更新版本\) 的虛擬資料表中的位移。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`如果這個 thunk 標記為非揮發性 \(只有在 DIA SDK V8.0 或更新\)。|  
  
## 請參閱  
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [THUNK\_ORDINAL 列舉](../../debugger/debug-interface-access/thunk-ordinal.md)