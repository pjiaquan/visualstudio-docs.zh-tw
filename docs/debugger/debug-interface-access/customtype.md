---
title: "CustomType | Microsoft Docs"
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
  - "CustomType 符號"
ms.assetid: 1b66bc0a-7979-416f-bf7f-e5df91584c91
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CustomType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

廠商定義的型別 \(編緝器特定型別\) 由`SymTagCustomType`符號。  
  
## 屬性  
 下表顯示其他有效的屬性，此符號的類型。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|`DWORD`|OEM 的識別項。|  
|[IDiaSymbol::get\_oemSymbolId](../Topic/IDiaSymbol::get_oemSymbolId.md)|`DWORD`|OEM 的內部 id。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagCustomType` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|參考自訂型別符號的第一個型別。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|型別符號的識別碼。|  
|[IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|`IDiaSymbol**`|所有的自訂型別符號所參考的型別陣列。|  
  
## 請參閱  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)