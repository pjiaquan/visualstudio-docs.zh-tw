---
title: "IActiveScriptProfilerControl3::EnumHeap 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl3::EnumHeap 方法
傳回可用來逐一查看 GC 堆積物件在關聯的指令碼引擎中的介面 \([IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\)。  
  
 您可以呼叫這個方法會在偵錯或發行模式。  這個方法，在 UI 執行緒閒置時，應該呼叫。  在呼叫方法之後，就不應該執行作業的物件除了 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 的指令碼引擎，直到 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 傳回 S\_FALSE 或釋放 [IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) 介面指標。  
  
## 語法  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### 參數  
 ppEnum  
 \[out\] 傳回 [IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)。  
  
## 傳回值  
 HRESULT。