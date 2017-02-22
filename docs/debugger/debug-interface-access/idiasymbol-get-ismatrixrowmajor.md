---
title: "IDiaSymbol::get_isMatrixRowMajor | Microsoft Docs"
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
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isMatrixRowMajor
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定這個矩陣的資料列是否為主要版本號碼。  
  
## 語法  
  
```cpp  
HRESULT get_isMatrixRowMajor(   
   BOOL* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 指派給 `BOOL` 指標這個矩陣的資料列是否為主要版本號碼。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)