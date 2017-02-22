---
title: "ArrayType | Microsoft Docs"
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
  - "ArrayType 符號"
ms.assetid: 1d973a3a-2bde-46df-8625-85d519bb3cc9
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ArrayType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

陣列由`SymTagArray`符號。  
  
## 屬性  
 下表顯示其他有效的屬性，此符號的類型。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_arrayIndexType](../Topic/IDiaSymbol::get_arrayIndexType.md)|`IDiaSymbol*`|陣列索引型別符號。|  
|[IDiaSymbol::get\_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|`DWORD`|陣列索引的型別符號的識別碼。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`如果陣列標記為常數。|  
|[IDiaSymbol::get\_count](../Topic/IDiaSymbol::get_count.md)|`DWORD`|陣列中的項目數目。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|以位元組為單位，此陣列的大小。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入編譯的符號。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|`DWORD`|FORTRAN 多維陣列的陣序。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagArray` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|陣列元素型別符號。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|陣列元素型別符號的識別碼。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`如果陣列是未對齊|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`如果陣列標示為非揮發性。|  
  
## 請參閱  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [維度](../../debugger/debug-interface-access/dimension.md)