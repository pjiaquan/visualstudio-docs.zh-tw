---
title: "IDiaSymbol::get_isHLSLData | Microsoft Docs"
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
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isHLSLData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定這個符號表示高階著色引擎Language \(HLSL\)資料。  
  
## 語法  
  
```cpp  
HRESULT get_isHLSLData(   
   BOOL* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 指派給 `BOOL` 指標這個符號表示 HLSL 資料。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)