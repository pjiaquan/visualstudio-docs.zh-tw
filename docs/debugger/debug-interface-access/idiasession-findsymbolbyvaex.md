---
title: "IDiaSession::findSymbolByVAEx | Microsoft Docs"
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
  - "IDiaSession::findSymbolByVAEx 方法"
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findSymbolByVAEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的符號型別，包含空白字元，或最接近，指定的虛擬位址 \(VA\) 和位移。  
  
## 語法  
  
```cpp#  
HRESULT findSymbolByVAEx (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### 參數  
 `va`  
 \[in\]指定的 VA.  
  
 `symtag`  
 \[in\]若要找的符號型別。  值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。  
  
 `ppSymbol`  
 \[\] out傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)擷取物件，表示該符號。  
  
 `displacement`  
 \[\] out傳回值，指定從所提供的虛擬位址的位移`va`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );  
```  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)