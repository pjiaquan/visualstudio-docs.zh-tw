---
title: "Enum (偵錯介面存取 SDK) | Microsoft Docs"
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
  - "列舉類型做為符號"
  - "Enum 符號"
ms.assetid: c777e2e6-88be-435b-b632-8d43f42b0b49
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Enum (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列舉型別由`SymTagEnum`的符號。  每個列舉值會顯示為類別子系與`SymTagConstant`標記。  
  
## 屬性  
 下表顯示其他有效的屬性，此符號的類型。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|其中一個 [BasicType 列舉](../../debugger/debug-interface-access/basictype.md) 值。|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|類別的父系這個列舉型別，如果有的話。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|類別父系符號的識別碼。|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE`如果列舉型別具有建構函式。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`如果列舉型別標記為常數。|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE`如果列舉型別有一個設定運算子。|  
|[IDiaSymbol::get\_hasCastOperator](../Topic/IDiaSymbol::get_hasCastOperator.md)|`BOOL`|`TRUE`如果列舉型別都具有轉換運算子。|  
|[IDiaSymbol::get\_hasNestedTypes](../Topic/IDiaSymbol::get_hasNestedTypes.md)|`BOOL`|`TRUE`如果列舉型別具有巢狀型別。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|這個列舉型別，以位元組為單位的長度。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入的符號[編譯模組](../../debugger/debug-interface-access/compiland.md)。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|列舉型別的名稱。|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE`如果在巢狀列舉型別。|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE`如果列舉型別會有任何多載的運算子。|  
|[IDiaSymbol::get\_packed](../Topic/IDiaSymbol::get_packed.md)|`BOOL`|`TRUE`如果封裝的列舉型別。|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE`如果非語彙範圍中出現的列舉型別。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagEnum` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|符號的基礎型別。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型別符號的識別碼。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`如果未對齊列舉型別。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`如果列舉型別標記為非揮發性。|  
  
## 請參閱  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)