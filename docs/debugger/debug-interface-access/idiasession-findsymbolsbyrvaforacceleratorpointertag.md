---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

將對應的標記值，這個方法會傳回在指定的相對虛擬位址的指定父快速 Stub 函式包含符號的列舉型別。  
  
## 語法  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### 參數  
 `parent`  
 \[in\] 對應至要搜尋的快速 Stub 函式的 `IDiaSymbol` 。  
  
 `tagValue`  
 \[in\] 指標標記值。  
  
 `rva`  
 \[in\] 相對虛擬位址。  
  
 `ppResult`  
 \[out\] 會使用這個結果的 `IDiaEnumSymbols` 介面指標的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 備註  
 呼叫這個方法只在對應至快速Stub函式的 `IDiaSymbol` 介面。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)