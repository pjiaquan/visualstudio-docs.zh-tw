---
title: "IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::ScriptCompiled
向分析工具告知物件指令碼引擎編譯指令碼。  這個方法會對已編譯的每個指令碼呼叫。  
  
## 語法  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### 參數  
 `scriptId`  
 \[in\] 已編譯之指令碼的唯一 ID。  這個 ID 是由指令碼引擎指派。  
  
 `type`  
 \[in\] 已編譯之指令碼的型別。  值在 [PROFILER\_SCRIPT\_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)中定義。  
  
 `pIDebugDocumentContext`  
 \[in\] \(如果有的話\)，對程式碼剖析工具必須 [IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md) 指標查詢的 `IUnknown` 介面的指標。  否則，這是空的。  
  
## 傳回值  
 這個方法的傳回值是由指令碼引擎會忽略。  
  
## 備註  
 並且只有在主應用程式，支援指令碼引擎可以提供文件內容。  
  
## 請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)