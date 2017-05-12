---
title: "PROFILER_HEAP_ENUM_FLAGS 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_ENUM_FLAGS 列舉
旗標，表示物件關聯性中指向的物件堆積的額外資訊是否公開。  使用 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) 方法。  
  
## 語法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,  
} PROFILER_HEAP_ENUM_FLAGS;  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|PROFILER\_HEAP\_ENUM\_FLAGS\_NONE|0x00000000|這個堆積物件不會公開有關物件關聯性的額外資訊。  這個堆積物件以與 [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)類似的行為方式。|  
|PROFILER\_HEAP\_ENUM\_ENUM\_ STORE\_RELATIONSHIP\_FLAGS|0x00000001|這個堆積物件會公開有關在物件關聯性中指向的物件是 getter 還是 setter 方法。  這項資訊會高會儲存 2 個位元組 \(16 位元\) [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) 欄位做為其中一個 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) 列舉值。|