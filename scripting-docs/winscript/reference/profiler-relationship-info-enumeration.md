---
title: "PROFILER_RELATIONSHIP_INFO 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_RELATIONSHIP_INFO 列舉
代表與物件有關的資訊在關聯性。  用於 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。  
  
## 語法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,  
    PROFILER_PROPERTY_TYPE_STRING = 0x02,  
    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,  
    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,  
    PROFILER_PROPERTY_TYPE_BSTR = 0x05,  
} PROFILER_RELATIONSHIP_INFO;  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|PROFILER\_PROPERTY\_TYPE\_NUMBER|0x01|物件是數字。|  
|PROFILER\_PROPERTY\_TYPE\_STRING|0x02|物件是字串。|  
|PROFILER\_PROPERTY\_TYPE\_HEAP\_OBJECT|0x03|物件是物件堆積。|  
|PROFILER\_PROPERTY\_TYPE\_EXTERNAL\_OBJECT|0x04|物件是外部的，也就是說，不在記憶體回收堆積上。|  
|PROFILER\_PROPERTY\_TYPE\_BSTR|0x05|物件是 BSTR。|