---
title: "IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.SetProfilerEventMask
apilocation: scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptProfilerControl::SetProfilerEventMask
將指定的事件類型指令碼引擎應該引發的 4 位元組的位元遮罩。  
  
## 語法  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### 參數  
 `dwEventMask`  
 \[in\] 指定事件型別的 4 位元組的位元遮罩。  位在 [PROFILER\_EVENT\_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)中定義。  
  
## 傳回值  
 傳回 HRESULT。  可能的值如下所示：  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|方法成功。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|程式碼剖析未啟用。|  
  
## 請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)