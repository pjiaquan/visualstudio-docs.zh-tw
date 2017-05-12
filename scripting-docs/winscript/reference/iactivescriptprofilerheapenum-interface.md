---
title: "IActiveScriptProfilerHeapEnum 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum 介面
在堆積中物件的 Iterator 與指令碼引擎，收集 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)。  
  
## 語法  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## 方法  
 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 取得下一個物件或物件在集合 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)收集堆積上的物件。  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo 方法](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 取得與指定之物件的選擇性資訊。 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)組工作集堆積上的物件。  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo 方法](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 釋放指定的 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md) 結構及其關聯的 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md) 項目。  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 傳回字串名稱與 [PROFILER\_HEAP\_OBJECT\_NAME\_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md) 值相對應。