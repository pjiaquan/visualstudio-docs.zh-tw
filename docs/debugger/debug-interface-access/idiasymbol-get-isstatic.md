---
title: "IDiaSymbol::get_isStatic | Microsoft Docs"
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
  - "IDiaSymbol::get_isStatic 方法"
ms.assetid: 3be5fe1b-46e8-4b07-90d8-4929dbbe7ff7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isStatic
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指定是否在函式或 thunk 層已被標示為靜態。  
  
## 語法  
  
```cpp  
HRESULT get_isStatic(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`如果函式或 thunk 層已標示為靜態。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)