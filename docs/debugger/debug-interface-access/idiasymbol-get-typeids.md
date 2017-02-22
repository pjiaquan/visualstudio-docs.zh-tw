---
title: "IDiaSymbol::get_typeIds | Microsoft Docs"
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
  - "IDiaSymbol::get_typeIds 方法"
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取此符號的編緝器特定的型別識別項值的陣列。  
  
## 語法  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### 參數  
 `cTypeIds`  
 \[in\]若要保留的資料緩衝區的大小。  
  
 `pcTypeIds`  
 \[\] out傳回的`typeIds`寫入，或者，如果`typeIds`是`NULL`，然後可以使用的型別識別項的總數。  
  
 `typeIds[]`  
 \[\] out陣列，則會填入這些型別識別項。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)