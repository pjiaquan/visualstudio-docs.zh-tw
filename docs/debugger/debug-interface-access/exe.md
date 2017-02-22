---
title: "Exe | Microsoft Docs"
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
  - ".dll 檔案"
  - "Exe 符號"
  - ".exe 檔案"
  - "可執行檔，Exe 符號"
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Exe 是唯一的符號而不是語彙或類別的父項目，當它表示全域範圍的.exe 或.dll 的檔案。  沒有使用的只有一個符號`SymTagExe`標記每個檔案。  [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)方法會傳回該符號。  
  
## 屬性  
 下表會對此符號的型別有效的屬性。  
  
|屬性|資料型別|描述|  
|--------|----------|--------|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|這個可執行檔的保留天數。|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID`這個可執行檔。|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE`如果符號檔相關聯則這個可執行檔會包含 c 型別 \(只在 DIA SDK v8.0 或更新版本\)。|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE`如果這個可執行檔 \(只有在 DIA SDK v8.0 或更新版本\) 相關聯的符號檔已移除專用符號。|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|指出目標 CPU 的值 \(其中[CV\_CPU\_TYPE\_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)值\)。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|.Exe 檔案的名稱。|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|可執行檔的簽章。|  
|[IDiaSymbol::get\_symbolsFileName](../Topic/IDiaSymbol::get_symbolsFileName.md)|`BSTR`|.Exe 檔案的.pdb 或.dbg 檔案的完整路徑。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|傳回`SymTagExe` \(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值\)。|  
  
## 請參閱  
 [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)   
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)