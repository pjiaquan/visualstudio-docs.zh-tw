---
title: "marker_importance 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_importance"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_importance 列舉"
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_importance 列舉
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示並行視覺化檢視標記的重要性層級。  
  
## 語法  
  
```  
enum marker_importance;  
```  
  
## Members  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`critical_importance`|指定標記的重要性為重大。|  
|`high_importance`|指定標記的重要性為高。|  
|`low_importance`|指定標記的重要性為低。|  
|`normal_importance`|指定標記的重要性為一般。|  
  
## 需求  
 **標題:** cvmarkersobj.h  
  
 **命名空間:** Concurrency::diagnostic  
  
## 請參閱  
 [diagnostic 命名空間](../profiling/diagnostic-namespace.md)