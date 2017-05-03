---
title: "IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionExit
通知分析工具的物件進行的指令碼引擎執行不是呼叫文件物件模型 \(DOM\) \(DOM\) 的函式呼叫。  
  
## 語法  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### 參數  
 `scriptId`  
 \[in\] 指令碼的唯一 ID 函式是的一部分。  這個 ID 是由指令碼引擎指派。  
  
 `functionId`  
 \[in\] 此函式的唯一 ID。  這個 ID 是由指令碼引擎指派。  
  
## 傳回值  
 這個方法的傳回值是由指令碼引擎會忽略。  
  
## 備註  
 對於 DOM 呼叫時，指令碼引擎呼叫 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) 而不是 `IActiveScriptProfilerCallback::OnFunctionExit`。  這是因為大量唯一方法和屬性都會 DOM。  
  
## 請參閱  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)