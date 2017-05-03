---
title: "IActiveScriptProfilerControl5::EnumHeap2 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerControl5::EnumHeap2 方法
傳回可在相關指令碼引擎內容中用來逐一查看 GC 堆積物件的介面 \([IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\)。  
  
 您可以在偵錯或發行模式中呼叫這個方法。  當 UI 執行緒閒置時，應該呼叫這個方法。  在呼叫方法之後，必須等到 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 傳回 S\_FALSE 或釋放 [IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) 介面指標，才能對指令碼引擎執行任何作業 \([IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 除外\)。  
  
## 語法  
  
```  
HRESULT EnumHeap2(  
    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,  
    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### 參數  
 enumFlags  
 值，指定是否公開物件關聯性所指向之物件的額外資訊。  額外資訊可能表示指向的物件是 getter 或 setter 方法。  如需詳細資訊，請參閱 [PROFILER\_HEAP\_ENUM\_FLAGS 列舉](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)。  
  
 ppEnum  
 \[out\] 傳回 [IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)。  
  
## 傳回值  
 傳回 HRESULT。  可能的值如下所示：  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功完成的堆積列舉。|  
|`E_OUTOFMEMORY`|沒有執行堆積列舉足夠的記憶體可用。|  
|`E_FAIL`|發生內部錯誤。|