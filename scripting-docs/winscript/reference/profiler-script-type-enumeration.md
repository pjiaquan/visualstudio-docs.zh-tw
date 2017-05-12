---
title: "PROFILER_SCRIPT_TYPE 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# PROFILER_SCRIPT_TYPE 列舉
指定指令碼的型別。  
  
## 語法  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## Members  
  
|成員|描述|  
|--------|--------|  
|PROFILER\_SCRIPT\_TYPE\_USER|指定使用者撰寫的指令碼。|  
|PROFILER\_SCRIPT\_TYPE\_DYNAMIC|指定在執行階段動態產生的指令碼。|  
|PROFILER\_SCRIPT\_TYPE\_NATIVE|是由指令碼引擎所定義的原生函式和物件指定指令碼類型。|  
|PROFILER\_SCRIPT\_TYPE\_DOM|指定呼叫文件物件模型 \(DOM\) Internet Explorer \(DOM\)，例如，呼叫 `document.getElementById` 方法。|  
  
## 請參閱  
 [動態指令碼分析工具的常數、列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)