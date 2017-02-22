---
title: "IDiaSymbol::get_dataBytes | Microsoft Docs"
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
  - "IDiaSymbol::get_dataBytes 方法"
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_dataBytes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取資料的位元組無限 OEM 標誌。  
  
## 語法  
  
```cpp#  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 參數  
 `cbData`  
 \[in\]若要保留的資料緩衝區的大小。  
  
 `pcbData`  
 \[\] out傳回寫入位元組數目，或者，如果`data`參數是`NULL`，傳回可用的位元組數。  
  
 `data[]`  
 \[\] out會被填入的資料位元組的緩衝區。  
  
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