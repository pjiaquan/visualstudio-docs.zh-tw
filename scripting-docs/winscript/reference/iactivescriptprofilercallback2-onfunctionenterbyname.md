---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionEnterByName"
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerCallback2::OnFunctionEnterByName
向分析工具告知物件指令碼引擎執行文件物件模型 \(DOM\) \(DOM\) 函式呼叫。  
  
## 語法  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### 參數  
 `pwszFunctionName`  
 \[in\] 指令碼引擎執行函式的名稱。  
  
 `scriptType`  
 \[in\] 此函式的型別。  如需有效值的說明，請參閱 [PROFILER\_SCRIPT\_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)。  
  
## 傳回值  
 這個方法的傳回值是由指令碼引擎會忽略。  
  
## 備註  
 對於 DOM 呼叫時，指令碼引擎會呼叫這個方法而不是呼叫 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)。  這是因為大量唯一方法和屬性都會 DOM。  
  
## 請參閱  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)