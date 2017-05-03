---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO 結構
這個類別代表物件堆積的任意資訊。  
  
## 語法  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO  
{  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;  
    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union  
    {  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;  
    };  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
  
```  
  
## Members  
  
|成員|型別|描述|  
|--------|--------|--------|  
|infoType|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE 列舉](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|選擇性的資訊類型。|  
|Prototype \- 原型|[PROFILER\_HEAP\_OBJECT\_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的原型物件的 ID。|  
|functionName|LPCWSTR|堆積物件的函式名稱。|  
|elementAttributesSize|UINT|堆積物件之項目屬性的大小。|  
|elementTextChildrenSize|UINT|堆積物件的文字子系的大小。|  
|scopeList|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|堆積物件的範圍清單。|  
|internalProperty|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)|堆積物件的內部屬性。|  
|namePropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆積物件名稱屬性清單。|  
|indexPropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆積中物件的索引屬性清單。|  
|relationshipList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|堆積物件的關聯性清單。|  
|eventList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|處理物件的事件清單。|