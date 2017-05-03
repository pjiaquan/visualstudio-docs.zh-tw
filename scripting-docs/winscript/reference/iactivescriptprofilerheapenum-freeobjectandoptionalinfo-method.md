---
title: "IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法
釋放指定的 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md) 結構及其關聯的 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 項目。  
  
## 語法  
  
```  
HRESULT FreeObjectAndOptionalInfo (  
    [in] ULONG celt,  
    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
  
```  
  
#### 參數  
 `celt`  
 釋放的物件數目。  
  
 `heapObjects`  
 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md) 結構的陣列。  
  
## 傳回值  
 HRESULT。