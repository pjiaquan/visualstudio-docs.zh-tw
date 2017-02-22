---
title: "IDiaSession::symsAreEquiv | Microsoft Docs"
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
  - "IDiaSession::symsAreEquiv 方法"
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

檢查兩個符號是否相等。  
  
## 語法  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### 參數  
 `symbolA`  
 \[in\]第一個[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)用於比較的物件。  
  
 `symbolB`  
 \[in\]第二個`IDiaSymbol`用於比較的物件。  
  
## 傳回值  
 如果符號是相等的會傳回`S_OK`。 否則，會傳回`S_FALSE`，這些符號並不相同。  否則，傳回錯誤碼。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)