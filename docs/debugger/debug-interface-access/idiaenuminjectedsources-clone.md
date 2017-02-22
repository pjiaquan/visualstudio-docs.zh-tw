---
title: "IDiaEnumInjectedSources::Clone | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Clone 方法"
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumInjectedSources::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立列舉值，包含目前的列舉值的列舉型別狀態。  
  
## 語法  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumInjectedSources** ppenum  
);  
```  
  
#### 參數  
 `ppenum`  
 \[\] out傳回[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)物件，包含列舉值已經存在。  插入的來源不會重複，將列舉值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)