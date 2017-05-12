---
title: "PROFILER_HEAP_OBJECT_FLAGS 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# PROFILER_HEAP_OBJECT_FLAGS 列舉
旗標表示堆積相關物件的基本資訊。  使用在 [PROFILER\_HEAP\_OBJECT 結構](../../winscript/reference/profiler-heap-object-structure.md)。  
  
## 語法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,  
    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,  
    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,  
    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,  
    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,  
    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,  
} PROFILER_HEAP_OBJECT_FLAGS;  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_NEW\_OBJECT|0x00000001|這個堆積配置的物件，在前一個堆積列舉要求之後。  [PROFILER\_HEAP\_OBJECT\_ID 類型](../../winscript/reference/profiler-heap-object-id-type.md) 值，如果物件集合，可以重複使用。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_IS\_ROOT|0x00000002|這個堆積物件是物件 Graph 的根物件。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SITE\_CLOSED|0x00000004|這個堆積物件是關閉的指令碼網站。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL|0x00000008|這個堆積 JavaScript 物件在記憶體回收堆積上配置之外為止。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL\_UNKNOWN|0x00000010|這個堆積物件在記憶體回收堆積外部配置及實作 IUnknown。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL\_DISPATCH|0x00000020|這個堆積物件在記憶體回收堆積上配置以外的 IDISPATCH 並實作介面。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SIZE\_APPROXIMATE|0x00000040|這個物件堆積的大小是類似的。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SIZE\_UNAVAILABLE|x00000080|這個堆積大小的物件無法使用。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_INSTANCE|0x00000200|堆積物件是 Windows 執行階段執行個體。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_RUNTIMECLASS|0x00000400|堆積物件是 Windows 執行階段執行階段類別。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_DELEGATE|0x00000800|堆積物件是 Windows 執行階段委派。|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_NAMESPACE|0x00001000|堆積物件在 Windows 執行階段命名空間。|