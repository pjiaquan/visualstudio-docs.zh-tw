---
title: "IDiaSymbol::get_isStripped | Microsoft Docs"
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
  - "IDiaSymbol::get_isStripped 方法"
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isStripped
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指出是否專用符號被剔除的符號檔。  
  
## 語法  
  
```cpp#  
HRESULT get_isStripped(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`如果移除專用符號從符號檔 ； 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 這個屬性是從`SymTagExe`的符號型別 \(請參閱[Exe](../../debugger/debug-interface-access/exe.md)\)。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)