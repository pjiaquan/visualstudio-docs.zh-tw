---
title: "PROFILER_EVENT_MASK 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# PROFILER_EVENT_MASK 列舉
表示應該設定檔事件的型別。  
  
## 語法  
  
```  
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## Members  
  
|成員|描述|  
|--------|--------|  
|PROFILER\_EVENT\_MASK\_TRACE\_SCRIPT\_FUNCTION\_CALL|設定檔會定義於使用者撰寫的指令碼和動態程式碼的函式。|  
|PROFILER\_EVENT\_MASK\_TRACE\_NATIVE\_FUNCTION\_CALL|設定檔是由指令碼引擎所定義的原生函式。|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL|設定檔是否有任何使用者定義的和指令碼引擎，不包括函式呼叫到文件物件模型 \(DOM\) \(DOM\)。|  
|PROFILER\_EVENT\_MASK\_TRACE\_DOM\_FUNCTION\_CALL|設定檔呼叫 DOM 的函式。|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL\_WITH\_DOM|設定檔的任何函式，包括呼叫到 DOM。|  
  
## 請參閱  
 [動態指令碼分析工具的常數、列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)