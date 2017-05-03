---
title: "IActiveScriptProfilerHeapEnum::Next 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::Next 方法
取得下一個物件或一組物件從 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)堆積上的物件。  
  
## 語法  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,   
    [out] ULONG *pceltFetched);  
  
```  
  
#### 參數  
 `celt`  
 要傳回的物件數。  
  
 `heapObjects`  
 \[in\] 下 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md) 結構。  
  
 `pceltFetched`  
 \[in\] 物件數目傳回，  
  
## 傳回值  
 HRESULT。