---
title: "IDiaSymbol::get_arrayIndexTypeId | Microsoft Docs"
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
  - "IDiaSymbol::get_arrayIndexTypeId 方法"
ms.assetid: 124f86e2-6f66-4541-87c3-799f435b731e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_arrayIndexTypeId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取陣列索引型別識別項的符號。  
  
## 語法  
  
```cpp#  
HRESULT get_arrayIndexTypeId (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的陣列索引型別 ID 的符號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 備註  
 識別項是唯一的值，由 DIA SDK 將標示為唯一的所有符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)