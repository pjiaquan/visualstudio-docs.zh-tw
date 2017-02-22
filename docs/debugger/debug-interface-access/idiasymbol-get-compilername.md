---
title: "IDiaSymbol::get_compilerName | Microsoft Docs"
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
  - "IDiaSymbol::get_compilerName 方法"
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_compilerName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

傳回編譯器用來產生名稱[編譯模組](../../debugger/debug-interface-access/compiland.md)。  
  
## 語法  
  
```cpp#  
HRESULT get_compilerName (  
   BSTR *pName  
);  
```  
  
#### 參數  
 `pName`  
 將包含編譯器的 Unicode 名稱的 bstr 的指標。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)