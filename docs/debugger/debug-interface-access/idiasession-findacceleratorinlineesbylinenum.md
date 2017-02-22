---
title: "IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs"
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
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findAcceleratorInlineesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

傳回符號的列舉型別對應至指定之來源位置的內嵌的框架。  
  
## 語法  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### 參數  
 `parent`  
 \[in\] 對應至快速Stub函式需要被搜尋的 `IDiaSymbol` 。  
  
 `file`  
 \[in\] 來源位置的 `IDiaSourceFile` 。  
  
 `linenum`  
 \[in\] 來源位置的行號。  
  
 `colnum`  
 \[in\] 來源位置的資料行數目。  
  
 `ppResult`  
 \[out\] 會使用這個結果的 `IDiaEnumLineNumbers` 介面指標的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)