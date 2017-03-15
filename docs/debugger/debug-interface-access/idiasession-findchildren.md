---
title: "IDiaSession::findChildren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::findChildren 方法"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取符合的名稱和符號的型別指定的父代的識別項的所有子系。  
  
## 語法  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 參數  
 `parent`  
 \[in\][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示父代。  如果此上層符號函式、 模組或區塊中，則其語彙的子系就會傳回`ppResult`。  如果父符號的型別，會傳回其類別的子系。  如果這個參數為`NULL`，然後`symtag`必須設為`SymTagExe`或`SymTagNull`，它會傳回全域範圍 \(.exe 檔案\)。  
  
 `symtag`  
 \[in\]指定符號的標記要擷取的子系。  值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。  設定成`SymTagNull`來擷取所有的子系。  
  
 `name`  
 \[in\]指定要擷取的子系的名稱。  設定成`NULL`為要擷取的所有子系。  
  
 `compareFlags`  
 \[in\]指定的比較選項套用到符合的名稱。  從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉型別可以單獨使用或一起使用。  
  
 `ppResult`  
 \[\] out傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取包含的子系符號清單的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
 下列範例顯示如何尋找函式的區域變數`pFunc`的符合項目名稱`szVarName`。  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## 請參閱  
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)