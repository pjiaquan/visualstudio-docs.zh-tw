---
title: "標籤 (偵錯介面存取 SDK) | Microsoft Docs"
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
  - "位置，在程式碼中"
  - "標籤符號"
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 標籤 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

程式碼的位置由`SymTagLabel`符號。  
  
## 屬性  
 下表會對此符號的型別有效的屬性。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|位移的組件的位置。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|區段的組件的位置。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`如果標籤會使用自訂的呼叫慣例。|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`如果標籤會執行到目前為止傳回項目。|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`如果標籤包含從插斷傳回。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入編譯、 區塊或函式的符號。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|標籤都有靜態的位置。 如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)列舉型別。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|標籤的名稱。|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`如果標籤所指定的[noinline](/visual-cpp/cpp/noinline)屬性。|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`如果標籤所指定的[noreturn](/visual-cpp/cpp/noreturn)屬性。|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`如果標籤永遠不會在呼叫中。|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|位移的符號，在電腦的記憶體。 如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)， `LocIsRegRel`。|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`如果程式碼已最佳化的程式碼的偵錯資訊。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此標籤，在它的模組中的相對位置。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagFuncDebugLabel` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|此標籤可執行檔映像中的位置。|  
  
## 請參閱  
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)