---
title: "IDiaEnumTables::Skip | Microsoft Docs"
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
  - "IDiaEnumTables::Skip 方法"
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

略過指定的數目的列舉型別序列中的資料表。  
  
## 語法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 參數  
 `celt`  
 \[in\]略過列舉序列中的表格數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`如果沒有更多的資料表，略過。  
  
## 請參閱  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)