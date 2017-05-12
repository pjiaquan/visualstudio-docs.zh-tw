---
title: "PROFILER_HEAP_OBJECT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT 結構
表示 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)收集堆積上的物件。  
  
## 語法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;  
    union {  
        PROFILER_HEAP_OBJECT_ID objectId;  
        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;  
    USHORT flags;   
    USHORT optionalInfoCount;  
} PROFILER_HEAP_OBJECT;  
```  
  
## Members  
  
|成員|型別|描述|  
|--------|--------|--------|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積中的物件 ID。|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|物件的外部物件位址，例如 . C \+\+ 配置的物件，是在 JavaScript 堆積之外。|  
|typeNameId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|堆積物件型別名稱的 ID，從擷取 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)。  只有一個 `externalObjectAddress` 或 `typeName` 根據 `flags` 值存在。|  
|旗標。|[PROFILER\_HEAP\_OBJECT\_FLAGS 列舉](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|包含有關物件堆積基本資訊的旗標。|  
|optionalInfoCount|USHORT|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 的資料錄數目的堆積物件使用。|