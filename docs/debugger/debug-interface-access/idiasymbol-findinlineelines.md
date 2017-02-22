---
title: "IDiaSymbol::findInlineeLines | Microsoft Docs"
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
ms.assetid: 56ba4bc0-8f96-47c2-8b18-332b4e7c2d91
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findInlineeLines
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取可讓用戶端透過指定的行號資訊重複內嵌，直接或間接，在這個符號的列舉型別。  
  
## 語法  
  
```cpp#  
HRESULT findInlineeLines (   
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### 參數  
 `ppResult`  
 \[out\] 物件所包含資料列編號清單中擷取的 `IDiaEnumLineNumbers` 物件。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)