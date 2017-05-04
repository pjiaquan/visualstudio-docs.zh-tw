---
title: "IActiveScript::GetCurrentScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetCurrentScriptThreadID"
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetCurrentScriptThreadID
擷取目前執行中的執行緒上的指令碼引擎中定義的識別項。  識別項可以用來對指令碼執行緒執行控制方法的後續呼叫 \(例如 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 方法。  
  
## 語法  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### 參數  
 `pstidThread`  
 \[out\] 接收指令碼執行緒識別項變數位址與目前執行緒。  這個識別項的解譯會留給指令碼引擎，不過，它可以是 Windows 執行緒識別項的複本。  如果 Win32 執行緒結束，這個識別項會變成未指派，而且可以隨後指派至另一個執行緒。  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_POINTER` ，如果無效的指標被指定。  
  
## 備註  
 這個方法只能從非 Base 執行緒呼叫未使非基底 Callout 裝載物件或加入至 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 介面。  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)