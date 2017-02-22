---
title: "IDiaSymbol::get_isOptimizedAway | Microsoft Docs"
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
ms.assetid: c18b1e38-b152-4a13-aba0-59faded5b2e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isOptimizedAway
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定變數是否進行最佳化。  
  
## 語法  
  
```cpp  
HRESULT get_isOptimizedAway(   
   BOOL* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 指派給 `BOOL` 的指標變數是否進行最佳化。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)