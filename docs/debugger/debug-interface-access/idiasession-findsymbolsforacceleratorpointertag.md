---
title: "IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

傳回符號的列舉型別變數的指定標記值對應父快速 Stub 函式。  
  
## 語法  
  
```cpp#  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### 參數  
 `parent`  
 \[in\] 對應至要搜尋的快速 Stub 函式的 IDiaSymbol。  
  
 `tagValue`  
 \[in\] 指標標記值。  
  
 `ppResult`  
 \[out\] 會使用這個結果的 `IDiaEnumSymbols` 介面指標的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)