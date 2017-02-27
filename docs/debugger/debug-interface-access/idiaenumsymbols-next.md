---
title: "IDiaEnumSymbols::Next | Microsoft Docs"
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
  - "IDiaEnumSymbols::Next 方法"
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbols::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的列舉型別序列中的符號數目。  
  
## 語法  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,  
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### 參數  
 celt  
 \[in\]要擷取列舉值中的符號數目。  
  
 rgelt  
 \[\] out陣列是好填入這些[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示您想要的符號。  
  
 pceltFetched  
 \[\] out傳回已擷取的列舉值中的符號數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`是否有任何符號。  否則，會傳回錯誤碼。  
  
## 範例  
  
```cpp#  
IDiaEnumSymbols* pEnum  
CComPtr< IDiaSymbol> pSym;  
DWORD celt;  
pEnum->Next( 1, &pSym, &celt );  
```  
  
## 請參閱  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)