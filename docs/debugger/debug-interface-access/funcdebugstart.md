---
title: "FuncDebugStart | Microsoft Docs"
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
  - "FuncDebugStart 符號"
  - "偵錯 [DIA SDK]，開始點"
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# FuncDebugStart
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

如果函式定義的點的偵錯就是開始點由使用的符號`SymTagFuncDebugStart`標記。  
  
## 屬性  
 下表會對此符號的型別有效的屬性。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|位移的組件的位置。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|區段的組件的位置。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`如果函式會使用自訂的呼叫慣例 \(僅在 DIA SDK v8.0 或更新版本\)。|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`如果函式在執行到目前為止傳回 \(只有在 DIA SDK v8.0 或更新\)。|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`如果函式會包含從插斷 \(只有在 DIA SDK v8.0 或更新版本\) 傳回。|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`如果函式標記為靜態 \(只有在 DIA SDK v8.0 或更新\)。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入函式的符號。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|起始點具有靜態的位置。 如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)。|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`如果函式所指定的[noinline](/visual-cpp/cpp/noinline) \(僅在 DIA SDK v8.0 或更新版本\) 的屬性。|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`如果函式所指定的[noreturn](/visual-cpp/cpp/noreturn) \(僅在 DIA SDK v8.0 或更新版本\) 的屬性。|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`如果永遠不會呼叫函式時 \(只有在 DIA SDK v8.0 或更新\)。|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|位移的符號，在電腦的記憶體。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)， `LocIsRegRel`。|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`如果程式碼已最佳化的程式碼 \(僅在 DIA SDK v8.0 或更新版本\) 的偵錯資訊。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|函式的區塊內的相對位置。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagFuncDebugStart` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|在可執行檔的函式的位置。|  
  
## 請參閱  
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)