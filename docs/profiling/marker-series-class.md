---
title: "marker_series 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series 類別"
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series 類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示單一提供者所產生一連串事件通道。  
  
## 語法  
  
```  
class marker_series;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[marker\_series::marker\_series 建構函式](../Topic/marker_series::marker_series%20Constructor.md)|初始化 `marker_series` 類別的新執行個體。|  
|[marker\_series::~marker\_series 解構函式](../profiling/marker-series-tilde-marker-series-destructor.md)|終結 marker\_series 物件並釋放所有已配置的資源。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[marker\_series::is\_enabled 方法](../Topic/marker_series::is_enabled%20Method.md)|判斷是否有任何工作階段已經啟用提供者。|  
|[marker\_series::write\_alert 方法](../profiling/marker-series-write-alert-method.md)|寫入並行視覺化檢視追蹤檔案的警示。|  
|[marker\_series::write\_flag 方法](../profiling/marker-series-write-flag-method.md)|將旗標寫入至並行視覺化檢視追蹤檔案。|  
|[marker\_series::write\_message 方法](../profiling/marker-series-write-message-method.md)|將訊息寫入至並行視覺化檢視追蹤檔案。|  
  
## 繼承階層架構  
 `marker_series`  
  
## 需求  
 **標題:** cvmarkersobj.h  
  
 **命名空間:** Concurrency::diagnostic  
  
## 請參閱  
 [diagnostic 命名空間](../profiling/diagnostic-namespace.md)