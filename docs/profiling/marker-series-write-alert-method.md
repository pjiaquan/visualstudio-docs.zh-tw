---
title: "marker_series::write_alert 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert"
helpviewer_keywords: 
  - "Concurrency::diagnostic:marker_series::write_alert 方法"
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::write_alert 方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

寫入並行視覺化檢視追蹤檔案的警示。  
  
## 語法  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### 參數  
 `_Format`  
 複合格式字串包含混合零或多個格式項目的文字，其與陣列中的物件相對應。  
  
## 需求  
 **標題:** cvmarkersobj.h  
  
 **命名空間:** Concurrency::diagnostic  
  
## 請參閱  
 [marker\_series 類別](../profiling/marker-series-class.md)