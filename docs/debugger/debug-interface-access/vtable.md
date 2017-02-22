---
title: "VTable | Microsoft Docs"
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
  - "VTable 符號"
  - "虛擬資料表"
ms.assetid: c8be6692-7d2a-4721-99d3-8e2e565bb8a1
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VTable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

虛擬資料表由`SymTagVTable`符號。  
  
## 屬性  
 下表顯示其他有效的屬性，此符號的類型。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|擁有此 VTable 類別的符號。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|類別父系符號的識別碼。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`如果類別的 VTable 標示為常數。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入編譯的符號。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagVTable` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|符號的 VTable [VTableShape](../../debugger/debug-interface-access/vtableshape.md)。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型別符號的識別碼。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`如果類別的 VTable 未對齊。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`如果類別的 VTable 標示為非揮發性。|  
  
## 請參閱  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [VTableShape](../../debugger/debug-interface-access/vtableshape.md)