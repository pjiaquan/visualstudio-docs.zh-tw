---
title: "SCRIPTTHREADID 的常數 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADID"
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# SCRIPTTHREADID 的常數
用來指定執行緒的型別。  
  
## 語法  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## 常數  
  
|常數|值|意義|  
|--------|-------|--------|  
|SCRIPTTHREADID\_CURRENT|0xFFFFFFFD|目前正在執行的執行緒。|  
|SCRIPTTHREADID\_BASE|0xFFFFFFFE|基本的執行緒;也就是指令碼引擎執行個體化的執行緒。|  
|SCRIPTTHREADID\_ALL|0xFFFFFFFF|所有執行緒。|  
  
## 備註  
 `IActiveScript::GetCurrentScriptThreadID`、 `IActiveScript::GetScriptThreadID`、 `IActiveScript::GetScriptThreadState`和 `IActiveScript::InterruptScriptThread`使用 `SCRIPTTHREADID` 型別，但是，常數可以由 `IActiveScript::GetScriptThreadState` 和 `IActiveScript::InterruptScriptThread`只能透過取得。  
  
## 請參閱  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)