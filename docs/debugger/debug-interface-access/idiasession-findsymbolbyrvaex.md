---
title: "IDiaSession::findSymbolByRVAEx | Microsoft Docs"
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
  - "IDiaSession::findSymbolByRVAEx 方法"
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolByRVAEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的符號型別，包含空白字元，或最接近，指定的相對虛擬位址 \(RVA\) 和位移。  
  
## 語法  
  
```cpp#  
HRESULT findSymbolByRVAEx (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### 參數  
 `rva`  
 \[in\]指定的 RVA。  
  
 `symtag`  
 \[in\]若要找的符號型別。  值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。  
  
 `ppSymbol`  
 \[\] out傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)擷取物件，表示該符號。  
  
 `displacement`  
 \[\] out傳回值，指定從控制台中的相對虛擬位址的位移`rva`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );  
```  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)