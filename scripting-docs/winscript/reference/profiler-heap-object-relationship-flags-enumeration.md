---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 列舉
旗標，表示物件關聯性中指向的物件堆積是 getter 或 setter 方法。  使用 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) 方法，在 PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS 值在 `enumFlags` 參數指定。  
  
## 語法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_NONE|0x00000000|這個在物件關聯性中指向的堆積物件沒有被識別為 getter 或 setter 方法。|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_GET\_ACCESSOR|0x00010000|在物件關聯性中指向的堆積物件是 getter 方法。  這項資訊會高會儲存 2 個位元組 \(16 位元\) [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) 欄位。|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_SET\_ACCESSOR|0x00020000|在物件關聯性中指向的堆積物件是 setter 方法。  這項資訊會高會儲存 2 個位元組 \(16 位元\) `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` 欄位。|