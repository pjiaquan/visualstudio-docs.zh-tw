---
title: "CompilandDetails | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CompilandDetails 符號"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

編譯時資訊被分為的符號`SymTagCompiland`標籤 \(較差的解析度\) 和`SymTagCompilandDetails`標籤 \(物體細部表現\)。  `SymTagCompilandDetails`需要載入其他符號。  但是，它提供了豐富的資訊並不具備的編譯`SymTagCompiland`符號。  
  
## 屬性  
 下表會對此符號的型別有效的屬性。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_backEndBuild](../Topic/IDiaSymbol::get_backEndBuild.md)|`DWORD`|編譯器後端組建編號。|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|編譯器後端的主要版本號碼。|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|編譯器後端的次要版本號碼。|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|編譯器產生此編譯時 \(只有在 DIA SDK V8.0 或更新版本\) 的名稱。|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|`TRUE`如果編譯已啟用 \[編輯後繼續\]。|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|編譯器前端的組建編號。|  
|[IDiaSymbol::get\_frontEndMajor](../Topic/IDiaSymbol::get_frontEndMajor.md)|`DWORD`|編譯器前端的主要版本號碼。|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|編譯器前端的次要版本號碼。|  
|[IDiaSymbol::get\_hasDebugInfo](../Topic/IDiaSymbol::get_hasDebugInfo.md)|`BOOL`|`TRUE`如果這個編譯偵錯資訊 \(僅在 DIA SDK V8.0 或更新版本\)。|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE`如果這個編譯時包含 managed 程式碼 \(僅在 DIA SDK v8.0 或更新版本\)。|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`如果編譯時所編譯的[\/GS \(緩衝區安全性檢查\)](/visual-cpp/build/reference/gs-buffer-security-check) \(僅在 DIA SDK V8.0 或更新版本\) 的編譯器參數。|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE`如果編譯時被轉為原生程式碼從通用中繼語言 \(CIL\) 的程式碼。|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE`如果使用者定義的型別 \(UDT\) 已對齊至某些指定記憶體界限 \(只有在 DIA SDK V8.0 或更新\)。|  
|[IDiaSymbol::get\_isHotpatchable](../Topic/IDiaSymbol::get_isHotpatchable.md)|`BOOL`|`TRUE`如果編譯時所編譯的[\/hotpatch \(建立可線上修補的影像\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) \(僅在 DIA SDK v8.0 或更新版本\) 的編譯器參數。|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE`如果編譯時所編譯的[\/LTCG \(連結時間產生程式碼\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) \(僅在 DIA SDK V8.0 或更新版本\) 的編譯器參數。|  
|[IDiaSymbol::get\_isMSILNetmodule](../Topic/IDiaSymbol::get_isMSILNetmodule.md)|`BOOL`|編譯為 Microsoft 中繼語言 \(MSIL\) 模組 \(只有在 DIA SDK v8.0 或更新版本\)，其值為 TRUE。|  
|[IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)|`DWORD`|原始程式碼語言。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|編譯的符號。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙的父代符號的識別碼。|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|在其編譯時所編譯的平台 \(其中[CV\_CPU\_TYPE\_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)值\)。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagCompilandDetails` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
  
## 備註  
 編譯器通常出現在表單中稱為兩段式編譯器 ； 在某些編譯器版本中，每個階段會處理其他的程式。  這些稱為前端和後端編譯器，分別，因此符號屬性後端及前端的版本號碼。  
  
## 請參閱  
 [編譯模組](../../debugger/debug-interface-access/compiland.md)   
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)