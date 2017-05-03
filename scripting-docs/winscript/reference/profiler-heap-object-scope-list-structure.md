---
title: "PROFILER_HEAP_OBJECT_SCOPE_LIST 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_SCOPE_LIST 結構
這個結構與只有函式物件。  範圍清單表示函式的關閉做為每個範圍與一個相關聯的屬性清單中的堆積物件代表每個指定範圍變數的範圍清單。  在某些情況下，物件名稱在該範圍中可能無法使用，而且只有，其索引至屬性清單中使用。  
  
## 語法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];  
} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
  
```  
  
## Members  
  
|成員|型別|描述|  
|--------|--------|--------|  
|count|UINT|範圍的數目。|  
|scopes|[PROFILER\_HEAP\_OBJECT\_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|範圍。|