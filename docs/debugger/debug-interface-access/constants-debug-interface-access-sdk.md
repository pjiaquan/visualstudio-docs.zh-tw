---
title: "常數 (偵錯介面存取 SDK) | Microsoft Docs"
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
  - "常數，DIA SDK"
  - "DIA SDK，常數"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 常數 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這些字串常數可以用來識別程式偵錯資料庫 \(PDB\) 檔案，透過 DIA SDK 的各個區段中。  
  
## 常數  
 下列被宣告為 C\/C\+\+ 的巨集。  
  
|巨集|值|  
|--------|-------|  
|`DiaTable_Symbols`|L"符號"|  
|`DiaTable_Sections`|L 「 節 」|  
|`DiaTable_SrcFiles`|L"SourceFiles"|  
|`DiaTable_LineNums`|L"LineNumbers"|  
|`DiaTable_SegMap`|L"SegmentMap"|  
|`DiaTable_Dbg`|L"Dbg"|  
|`DiaTable_InjSrc`|L"InjectedSource"|  
|`DiaTable_FrameData`|L"FrameData"|  
  
## 範例  
 以下是使用這些符號其中一項的範例：  
  
```cpp#  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## 需求  
 標頭: dia2.h  
  
## 請參閱  
 [參考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)