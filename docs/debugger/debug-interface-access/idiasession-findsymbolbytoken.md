---
title: "IDiaSession::findSymbolByToken | Microsoft Docs"
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
  - "IDiaSession::findSymbolByToken 方法"
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolByToken
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取包含指定之中繼資料語彙基元的符號。  
  
## 語法  
  
```cpp#  
HRESULT findSymbolByToken (   
   ULONG        token,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### 參數  
 `token`  
 \[in\]指定的語彙基元。  
  
 `symtag`  
 \[in\]若要找的符號型別。  值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。  
  
 `ppSymbol`  
 \[\] out傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)擷取物件，表示該符號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );  
```  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)