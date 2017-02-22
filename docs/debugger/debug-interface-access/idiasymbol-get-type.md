---
title: "IDiaSymbol::get_type | Microsoft Docs"
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
  - "IDiaSymbol::get_type 方法"
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_type
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取符號來代表此符號的類型。  
  
## 語法  
  
```cpp#  
HRESULT get_type (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示此符號的型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 如果要判斷型別具有一個符號，您必須呼叫這個方法，並檢查所產生的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。  請注意可能不具有類型符號。  例如，結構的名稱有沒有類型，但是可能會有子系的符號 \(使用[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)方法來檢查這些子系\)。  
  
## 範例  
  
```cpp#  
IDiaSymbol*         pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (SUCCEEDED(pType->get_type( &pBaseType ))) {  
    BasicType btBaseType;  
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {  
        // Do something with basic type.  
    }  
}  
```  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)