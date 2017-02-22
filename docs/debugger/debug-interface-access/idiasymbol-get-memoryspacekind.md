---
title: "IDiaSymbol::get_memorySpaceKind | Microsoft Docs"
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
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_memorySpaceKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取記憶體空間內的型別。  
  
## 語法  
  
```cpp  
HRESULT get_memorySpaceKind(   
   DWORD* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 保留的記憶體空間類型為 `DWORD` 的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)