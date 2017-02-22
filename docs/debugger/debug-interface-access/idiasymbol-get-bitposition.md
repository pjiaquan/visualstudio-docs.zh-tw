---
title: "IDiaSymbol::get_bitPosition | Microsoft Docs"
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
  - "IDiaSymbol::get_bitPosition 方法"
ms.assetid: b0059407-8655-497b-81ca-025595989371
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_bitPosition
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取位置的位元位置。  Used when the [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) is `LocIsBitField`.  
  
## 語法  
  
```cpp#  
HRESULT get_bitPosition (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回之位置的位元位置。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤的程式碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)