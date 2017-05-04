---
title: "動態指令碼分析工具的常數、列舉和結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 動態指令碼分析工具的常數、列舉和結構
以下列舉型別被現用指令碼分析工具介面使用。  
  
## 常數, 列舉和結構  
  
|常數|描述|  
|--------|--------|  
|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS 類型](../../winscript/reference/profiler-external-object-address-type.md)|分析工具的外部物件位址。  使用 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md) 和 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER\_HEAP\_OBJECT\_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md)|堆積物件的 ID。  使用 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md) [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md), 和 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER\_HEAP\_OBJECT\_NAME\_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md)|堆積物件名稱的 ID。  用於 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)。|  
  
|列舉|描述|  
|--------|--------|  
|[PROFILER\_EVENT\_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)|表示應該分析事件的型別。|  
|[PROFILER\_HEAP\_ENUM\_FLAGS 列舉](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|旗標，表示物件關聯性中指向的物件堆積的額外資訊是否公開。  使用 [IActiveScriptProfilerControl5::EnumHeap2 方法](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)。|  
|[PROFILER\_HEAP\_OBJECT\_FLAGS 列舉](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|旗標表示有關堆積物件的基本資訊。  使用 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)。|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE 列舉](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|表示選擇性不同類型的資訊。  用於 [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)。|  
|[PROFILER\_RELATIONSHIP\_INFO 列舉](../../winscript/reference/profiler-relationship-info-enumeration.md)|代表與物件有關的資訊在關聯性。  用於 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。|  
|[PROFILER\_SCRIPT\_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)|指定訊息的指令碼。|  
  
|結構|描述|  
|--------|--------|  
|[PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)|表示 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)工作集的堆積物件。|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO 結構](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|表示有關堆積物件的任意資訊。|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)|代表堆積物件的關聯性。|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST 結構](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|代表屬於堆積中的物件關係的清單。|  
|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST 結構](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|這個結構只與函式物件有關。  範圍清單表示函式的關閉做為每個範圍與一個相關聯的屬性清單的堆積物件表示每個特定範圍的變數範圍的清單。  在某些情況下，物件名稱在該範圍的可能無法使用，只有 ID 可以。|  
  
## 請參閱  
 [動態指令碼分析工具的介面](../../winscript/reference/active-script-profiler-interfaces.md)