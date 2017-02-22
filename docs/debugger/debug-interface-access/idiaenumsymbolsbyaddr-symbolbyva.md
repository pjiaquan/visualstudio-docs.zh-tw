---
title: "IDiaEnumSymbolsByAddr::symbolByVA | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::symbolByVA 方法"
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::symbolByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

藉由執行對應的虛擬位址 \(VA\) 中放置列舉值。  
  
## 語法  
  
```cpp#  
HRESULT symbolByVA (   
   DWORD**      virtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### 參數  
 virtualAddress  
 \[in\]虛擬位址。  
  
 ppsymbol  
 \[\] out傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表找到該符號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果找不到符號。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)