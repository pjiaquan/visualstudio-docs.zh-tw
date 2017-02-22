---
title: "IDiaSymbol::get_isSplitted | Microsoft Docs"
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
  - "IDiaSymbol::get_isSplitted 方法"
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isSplitted
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指定資料符號是否已分割成的彙總或集合的其他符號。 編譯器會視為符號分開的實體，即使它們屬於真正的較大的符號。  
  
## 語法  
  
```cpp  
HRESULT get_isSplitted(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`若符號已分割成彙總的符號。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤的程式碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 [IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)方法傳回`TRUE`屬於分割符號的所有符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)