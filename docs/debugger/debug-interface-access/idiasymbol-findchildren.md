---
title: "IDiaSymbol::findChildren | Microsoft Docs"
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
  - "IDiaSymbol::findChildren 方法"
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取該符號的子系。  
  
## 語法  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 參數  
 `symtag`  
 \[in\]指定要擷取的子系的符號標記所定義的[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)。  設定成`SymTagNull`為要擷取的所有子系。  
  
 `name`  
 \[in\]指定要擷取的子系的名稱。  設定成`NULL`為要擷取的所有子系。  
  
 `compareFlags`  
 \[in\]指定的比較選項套用到符合的名稱。  從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉型別可以單獨使用或一起使用。  
  
 `ppResult`  
 \[\] out傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取包含的子系符號清單的物件。  
  
## 傳回值  
 傳回`S_OK`若至少一個子節點的符號已經找到，或是傳回`S_FALSE`如果找不到沒有子系。 否則會傳回錯誤碼。  
  
## 備註  
 這個方法就等於電話[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)完成這個符號的第一個參數的方法。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)