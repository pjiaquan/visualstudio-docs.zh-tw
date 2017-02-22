---
title: "PointerType | Microsoft Docs"
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
  - "PointerType 符號"
ms.assetid: 67228681-7345-4537-8af3-93806803ee96
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# PointerType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

每一個指標由`SymTagPointerType`符號。  
  
## 屬性  
 下表顯示其他有效的屬性，此符號的類型。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`如果指標已標記為常數。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|以位元組為單位，將指標的大小。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入的符號[編譯模組](../../debugger/debug-interface-access/compiland.md)。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_reference](../Topic/IDiaSymbol::get_reference.md)|`BOOL`|`TRUE`如果指標是參考型別。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagPointerType` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|目標的象徵指標。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型別符號的識別碼。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`如果指標為沒有對齊。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`如果指標已標記為靜態。|  
  
## 請參閱  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)