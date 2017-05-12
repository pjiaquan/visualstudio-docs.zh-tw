---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP 結構
表示處理物件的關聯性。  
  
## 語法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP  
{  
    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;  
    PROFILER_RELATIONSHIP_INFO relationshipInfo;  
    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union  
    {  
        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;  
        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;  
        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;  
        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|relationshipId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|關聯性名稱的 ID，從 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)。|  
|relationshipInfo|[PROFILER\_RELATIONSHIP\_INFO 列舉](../../winscript/reference/profiler-relationship-info-enumeration.md)|如需關聯性的詳細資訊。|  
|numberValue|double|數值。  只有一個 `numberValue`\/`stringValue`\/`objectId`\/`externalObjectAddress` 根據 `relationshipInfo` 值設定為。|  
|stringValue|LPCWSTR|字串值。|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積中的物件 ID。|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|外部物件位址。|