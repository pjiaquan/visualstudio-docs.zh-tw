---
title: "IDiaSymbol::get_isAcceleratorStubFunction | Microsoft Docs"
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
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isAcceleratorStubFunction
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

表示符號是否對應於為對應到 `parallel_for_each` 呼叫的快速編譯著色器的最上層函式符號。  
  
## 語法  
  
```cpp  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### 參數  
 `pFlag`  
 \[out\] 表示 `BOOL` 指標符號是否對應於為對應到 `parallel_for_each` 呼叫的快速編譯著色器的最上層函式符號。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)