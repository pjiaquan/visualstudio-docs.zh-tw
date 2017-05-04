---
title: "IActiveScriptProfilerHeapEnum::GetNameIdMap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::GetNameIdMap
傳回字串名稱與 [PROFILER\_HEAP\_OBJECT\_NAME\_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md) 值對應。  
  
## 語法  
  
```  
HRESULT GetNameIdMap (  
    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],   
    [out] UINT *pcelt);  
```  
  
#### 參數  
 `pNameList`  
 \[out\] 此名稱與 [PROFILER\_HEAP\_OBJECT\_NAME\_ID 類型](../../winscript/reference/profiler-heap-object-name-id-type.md) 值。  
  
 `pcelt`  
 \[in\] 名稱陣列中的元素數目的。  
  
## 傳回值  
 HRESULT。