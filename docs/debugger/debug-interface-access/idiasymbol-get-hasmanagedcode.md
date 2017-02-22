---
title: "IDiaSymbol::get_hasManagedCode | Microsoft Docs"
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
  - "IDiaSymbol::get_hasManagedCode 方法"
ms.assetid: e40f82f5-88fe-4a9b-b594-3605f42773ec
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasManagedCode
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指出此模組是否包含 managed 程式碼。  
  
## 語法  
  
```cpp#  
HRESULT get_hasManagedCode(  
   BOOL *pFlag  
);  
```  
  
#### 參數  
 `pFlag`  
 \[\] out傳回`TRUE`如果模組包含 managed 程式碼路徑。 否則，會傳回`FALSE`，程式碼是不受管理的程式碼。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示的屬性不是可用的符號。  
  
## 備註  
 這個屬性是從`SymTagCompilandDetails`的符號型別 \(請參閱[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)\)。  
  
## 需求  
  
|需求|描述|  
|--------|--------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)