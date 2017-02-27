---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Prev 方法"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

藉由前一個符號的順序來擷取位址。  
  
## 語法  
  
```cpp#  
HRESULT Prev (   
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
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果沒有前一個符號。  否則，會傳回錯誤碼。  
  
## 備註  
 這個方法會更新所擷取的項目數的列舉值的位置。  
  
## 請參閱  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)