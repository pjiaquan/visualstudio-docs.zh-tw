---
title: "marker_series::write_message 方法 | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::write_message"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_message 方法"
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::write_message 方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將訊息寫入至並行視覺化檢視追蹤檔案。  
  
## 語法  
  
```  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
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
 重要性等級。  
  
 `_Category`  
 Category.Importance 層級。  
  
## 需求  
 **標題:** cvmarkersobj.h  
  
 **命名空間:** Concurrency::diagnostic  
  
## 請參閱  
 [marker\_series 類別](../profiling/marker-series-class.md)