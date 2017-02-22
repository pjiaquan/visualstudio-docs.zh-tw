---
title: "IDiaSymbol::get_restrictedType | Microsoft Docs"
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
ms.assetid: c48b00a6-26b0-47b0-b824-fe44dedbc756
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_restrictedType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定 `this` 指標是否會標示為來限制。  
  
## 語法  
  
```cpp  
HRESULT get_restrictedType(   
   BOOL* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 指派給 `BOOL` 的指標 `this` 指標是否會標示為來限制。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)