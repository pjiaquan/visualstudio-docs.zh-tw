---
title: "IDiaEnumSymbols::Skip | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaEnumSymbols::Skip 方法"
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbols::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

略過指定的數目的列舉型別序列中的符號。  
  
## 語法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 參數  
 celt  
 \[in\]略過列舉序列中的符號數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`是否有任何符號來略過。  
  
## 請參閱  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)