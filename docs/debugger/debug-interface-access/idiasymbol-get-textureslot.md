---
title: "IDiaSymbol::get_textureSlot | Microsoft Docs"
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
ms.assetid: 166a1a3a-2e10-4baa-ace1-9104b56185ce
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_textureSlot
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取紋理位置。  
  
## 語法  
  
```cpp  
HRESULT get_textureSlot(   
   DWORD* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 包含紋理的位置對應至 `DWORD` 的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)