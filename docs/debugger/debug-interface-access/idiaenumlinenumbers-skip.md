---
title: "IDiaEnumLineNumbers::Skip | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Skip 方法"
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumLineNumbers::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

略過指定的數目的列舉型別序列中的行號。  
  
## 語法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 參數  
 celt  
 \[in\]略過列舉序列中的行號的數字。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`是否有沒有更多的行號，以略過。  
  
## 請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)