---
title: "IDiaSymbol::get_compilerGenerated | Microsoft Docs"
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
  - "IDiaSymbol::get_compilerGenerated 方法"
ms.assetid: 864d9249-f0c8-4a34-b391-eb785f7e8865
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_compilerGenerated
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指出是否由編譯器器產生的符號。  
  
## 語法  
  
```cpp#  
HRESULT get_compilerGenerated (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果編譯器產生符號; 否則，會傳回`FALSE`若符號已由使用者撰寫的程式碼產生。  
  
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