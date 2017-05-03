---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fcb55f5f-ce75-4d05-9ce9-ba28c622f97d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 列舉
表示選擇性不同類型的資訊。  用於 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)。  
  
## 語法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE                    = 0x00000001,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME                = 0x00000002,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST                   = 0x00000003,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY            = 0x00000004,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES              = 0x00000005,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES             = 0x00000006,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE      = 0x00000007,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE   = 0x00000008,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS                = 0x00000009,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS                  = 0x0000000A,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE                    = PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE;  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_PROTOTYPE|0x00000001|如需堆積物件原型的詳細資訊。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_FUNCTION\_NAME|0x00000002|如需堆積物件的函式名稱的資訊。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_SCOPE\_LIST|此|如需堆積物件之 [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)的資訊。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_INTERNAL\_PROPERTY|0x00000004|如需堆積物件之內部屬性的資訊。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_NAME\_PROPERTIES|此|如需堆積物件名稱屬性的資訊。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_INDEX\_PROPERTIES|此|如需堆積中物件的索引屬性的資訊。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_ELEMENT\_ATTRIBUTES\_SIZE|此|與 DOM 項目屬性的大小。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_ELEMENT\_TEXT\_CHILDREN\_SIZE|0x00000008|與 DOM 項目任何文字的大小。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_RELATIONSHIPS|0x00000009|如需堆積物件的關聯性的相關資訊。|  
|ROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_WINRTEVENTS|0x0000000A|如需堆積物件的 Windows 執行階段事件的資訊。|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_MAX\_VALUE|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_WINRTEVENTS|這個列舉的最大值。|