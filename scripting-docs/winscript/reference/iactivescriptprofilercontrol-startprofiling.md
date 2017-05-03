---
title: "IActiveScriptProfilerControl::StartProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerControl::StartProfiling
設定檔在指令碼引擎的開頭。  指令碼引擎會藉由呼叫分析工具建立物件的執行個體。 [CoCreateInstance](http://msdn.microsoft.com/zh-tw/7295a55b-12c7-4ed0-a7a4-9ecee16afdec)。  
  
## 語法  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### 參數  
 `clsidProfilerObject`  
 \[in\] 類別識別項 \(Class Identifier，CLSID\) 所建立的程式碼剖析工具物件。  
  
 `dwEventMask`  
 \[in\] 指定事件型別的 4 位元組的位元遮罩。  位在 [PROFILER\_EVENT\_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)中定義。  
  
 `dwContext`  
 \[in\] 傳遞至分析工具物件的 4 位元組值。  
  
## 傳回值  
 傳回 HRESULT。  可能的值如下所示：  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|方法成功。|  
|`ACTIVPROF_E_PROFILER_PRESENT`|程式碼剖析已啟用。|  
  
## 請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)