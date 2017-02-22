---
title: "IDiaSymbol::get_builtInKind | Microsoft Docs"
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
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_builtInKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取一種內建HLSL型別。  
  
## 語法  
  
```cpp  
HRESULT get_buildInKind(   
   DWORD* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 保留一種內建 HLSL 型別為 `DWORD` 的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)