---
title: "IActiveScriptProfilerCallback::Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback::Shutdown
呼叫以告知程式碼剖析工具物件，只要設定檔在一個指令碼引擎已停止。  這樣一來，程式碼剖析工具物件可以呼叫其清除常式，必要時\)。  這個方法是由指令碼引擎也會呼叫，以便指令碼引擎關閉時，或當 [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) ，對的呼叫失敗時  
  
## 語法  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### 參數  
 `hrReason`  
 \[in\] 要關閉的原因。  如果指令碼引擎已關閉， `S_OK` 傳遞。  如果 [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) 對的呼叫傳回失敗的 HRESULT， HRESULT 會傳遞。  否則，此值會 [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)擷取。  
  
## 傳回值  
 這個方法的傳回值是由指令碼引擎會忽略。  
  
## 請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)