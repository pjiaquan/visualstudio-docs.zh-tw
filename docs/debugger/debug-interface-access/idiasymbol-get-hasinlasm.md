---
title: "IDiaSymbol::get_hasInlAsm | Microsoft Docs"
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
  - "IDiaSymbol::get_hasInlAsm 方法"
ms.assetid: 7001c7cc-1459-4929-851b-a08066a803c6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasInlAsm
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指定函式是否包含內嵌組譯碼。  
  
## 語法  
  
```cpp  
HRESULT get_hasInlAsm(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`如果函式的任何內嵌組譯碼。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)