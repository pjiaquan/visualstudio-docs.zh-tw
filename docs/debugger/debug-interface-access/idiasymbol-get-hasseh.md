---
title: "IDiaSymbol::get_hasSEH | Microsoft Docs"
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
  - "IDiaSymbol::get_hasSEH 方法"
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_hasSEH
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的函式是否包含任何的旗標[結構化例外狀況處理](/visual-cpp/cpp/structured-exception-handling-c-cpp) \(比方說，\_\_try \/ \_\_except 區塊\)。  
  
## 語法  
  
```cpp#  
HRESULT get_hasSEH(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`如果函式的任何結構化的例外處理區塊。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤的程式碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [結構化例外狀況處理](/visual-cpp/cpp/structured-exception-handling-c-cpp)