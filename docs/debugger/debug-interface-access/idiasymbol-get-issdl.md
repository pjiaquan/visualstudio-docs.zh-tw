---
title: "IDiaSymbol::get_isSdl | Microsoft Docs"
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
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isSdl
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定模組是否使用\/SDL選項編譯。  
  
## 語法  
  
```cpp  
HRESULT get_isSdl(  
   BOOL *pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 指派給 `BOOL` 指標模組是否使用\/SDL 選項編譯。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)