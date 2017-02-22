---
title: "Typedef (偵錯介面存取 SDK) | Microsoft Docs"
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
  - "Typedef 符號 [DIA SDK]"
ms.assetid: 9ab441b9-cc72-47fa-83e2-87b3c2b891b4
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Typedef (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

符號與`SymTagTypedef`標記引入其他類型的名稱。  
  
## 屬性  
 下表顯示其他有效的屬性，此符號的類型。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|其中一個 [BasicType 列舉](../../debugger/debug-interface-access/basictype.md) 值。|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|類別的父系這個 typedef，如果有的話。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|類別父系符號的識別碼。|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE`如果這個 typedef 具有建構函式。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`如果這個 typedef 標示為常數。|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE`如果這個 typedef 有一個設定運算子。|  
|[IDiaSymbol::get\_hasCastOperator](../Topic/IDiaSymbol::get_hasCastOperator.md)|`BOOL`|`TRUE`如果這個 typedef 都具有轉換運算子。|  
|[IDiaSymbol::get\_hasNestedTypes](../Topic/IDiaSymbol::get_hasNestedTypes.md)|`BOOL`|`TRUE`如果這個 typedef 有巢狀型別。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|這個 typedef，以位元組為單位的長度。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入編譯的符號。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Typedef 名稱。|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE`如果這個 typedef 語彙範圍中巢狀。|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE`如果這個 typedef 有一個多載的運算子。|  
|[IDiaSymbol::get\_packed](../Topic/IDiaSymbol::get_packed.md)|`BOOL`|`TRUE`如果這個 typedef 已壓縮。|  
|[IDiaSymbol::get\_reference](../Topic/IDiaSymbol::get_reference.md)|`BOOL`|`TRUE`如果這個 typedef 是參考。|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE`如果這個 typedef 處於非語彙範圍。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagTypedef` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|符號的基礎型別。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型別符號的識別碼。|  
|[IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|其中一個 [UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md) 值。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`如果這個 typedef 未對齊。|  
|[IDiaSymbol::get\_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|描述的虛擬資料表形狀符號。|  
|[IDiaSymbol::get\_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|虛擬資料表圖形符號的識別碼。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`如果這個 typedef 被標示為非揮發性。|  
  
## 備註  
 因為 typedef 可以表示類別、 指標或使用者定義的型別 \(UDT\)，typedef 符號會共用相同的屬性，做為其中一個符號這些其他型別。  
  
## 請參閱  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)