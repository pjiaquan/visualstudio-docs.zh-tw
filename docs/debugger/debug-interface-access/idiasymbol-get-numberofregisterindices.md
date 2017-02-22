---
title: "IDiaSymbol::get_numberOfRegisterIndices | Microsoft Docs"
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
ms.assetid: 1ec8b8ea-e423-4327-8dc0-a390e6e3ffb0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_numberOfRegisterIndices
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取暫存器索引的數目。  
  
## 語法  
  
```cpp  
HRESULT get_numberOfRegisterIndices(   
   DWORD* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 保留暫存器的索引數目。 `DWORD` 的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)