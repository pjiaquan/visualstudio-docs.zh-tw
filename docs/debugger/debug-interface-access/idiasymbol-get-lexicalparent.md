---
title: "IDiaSymbol::get_lexicalParent | Microsoft Docs"
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
  - "IDiaSymbol::get_lexicalParent 方法"
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_lexicalParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取語彙的父代的符號參考。  
  
## 語法  
  
```cpp#  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) ，表示符號的語彙的父代的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤的程式碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 語彙的父代的符號是封入函式或模組。  比方說，函式參數或區域變數的語彙的父代都是函式本身的函式語彙的父代時，用來定義它的模組。  
  
 可能的符號，能顯示為語彙的父代會詳加[符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)