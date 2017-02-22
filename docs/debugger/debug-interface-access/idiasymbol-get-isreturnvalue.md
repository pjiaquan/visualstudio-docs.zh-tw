---
title: "IDiaSymbol::get_isReturnValue | Microsoft Docs"
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
ms.assetid: 37aaf48a-65cb-4ec2-823e-1c637a9f939c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isReturnValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定變數是否帶有傳回值。  
  
## 語法  
  
```cpp  
HRESULT get_isReturnValue(   
   BOOL* pRetVal);  
```  
  
#### 參數  
 `pRetVal`  
 \[out\] 指派給 `BOOL` 的指標變數是否帶有傳回值。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)