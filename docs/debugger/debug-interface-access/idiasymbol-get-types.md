---
title: "IDiaSymbol::get_types | Microsoft Docs"
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
  - "IDiaSymbol::get_types 方法"
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取此符號的編緝器特定型別的陣列。  
  
## 語法  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### 參數  
 `cTypes`  
 \[in\]若要保留的資料緩衝區的大小。  
  
 `pcTypes`  
 \[\] out傳回的型別，或者，如果`types`參數是`NULL`，然後可用類型的總數。  
  
 `types[]`  
 \[\] out陣列是好填入這些[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示此符號的所有型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)