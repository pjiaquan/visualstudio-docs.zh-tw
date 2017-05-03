---
title: "IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::FunctionCompiled
向分析工具告知物件指令碼引擎遇到函式，在編譯指令碼時。  
  
## 語法  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### 參數  
 `functionId`  
 \[in\] 此函式的唯一 ID。  這個 ID 是由指令碼引擎指派。  
  
 `scriptId`  
 \[in\] 指令碼的唯一 ID 函式是的一部分。  
  
 `pwszFunctionName`  
 \[in\] 此函式則為 null 名稱匿名函式的。  
  
 `pwszFunctionNameHint`  
 \[in\] 函式 null 推斷名稱，如果指令碼引擎不會推斷任何名稱。  
  
 `pIDebugDocumentContext`  
 \[in\] \(如果有的話\)，對程式碼剖析工具必須 [IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md) 指標查詢的 `IUnknown` 介面的指標。  否則為 null。  
  
## 傳回值  
 這個方法的傳回值是由指令碼引擎會忽略。  
  
## 備註  
 並且只有在主應用程式，支援指令碼引擎可以提供文件內容。  
  
## 請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)