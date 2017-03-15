---
title: "marker_series::write_flag 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_flag 方法"
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series::write_flag 方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將旗標寫入至並行視覺化檢視追蹤檔案。  
  
## 語法  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### 參數  
 `_Format`  
 複合格式字串包含混合零或多個格式項目的文字，其與陣列中的物件相對應。  
  
 `_Importance`  
 重要性。  
  
 `_Category`  
 分類  
  
## 需求  
 **標題:** cvmarkersobj.h  
  
 **命名空間:** Concurrency::diagnostic  
  
## 請參閱  
 [marker\_series 類別](../profiling/marker-series-class.md)