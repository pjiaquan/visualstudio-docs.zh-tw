---
title: "IDiaSymbol::get_access | Microsoft Docs"
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
  - "IDiaSymbol::get_access 方法"
ms.assetid: 908976ae-95c4-4020-89c9-de137f727f98
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_access
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取類別成員的存取修飾詞。  
  
## 語法  
  
```cpp#  
HRESULT get_access (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回值，從[CV\_access\_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)指定存取修飾詞的類別成員的列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_access\_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)