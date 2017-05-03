---
title: "IActiveScript::GetScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadID"
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadID
擷取執行緒的指令碼引擎中定義的識別項與指定 Win32 執行緒。  
  
## 語法  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### 參數  
 `dwWin32ThreadID` ,  
 \[in\] 執行 Win32 執行緒的執行緒識別項在目前處理序的。  使用 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) 函式會擷取目前執行之執行緒的執行緒識別項。  
  
 `pstidThread` ,  
 \[out\] 接收指令碼執行緒識別項與指定 Win32 執行緒變數的位址。  這個識別項的解譯會留給指令碼引擎，不過，它可以是 Windows 執行緒識別項的複本。  請注意，如果 Win32 執行緒結束，這個識別項會變成未指派，而且可能後續指派至另一個執行緒。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\) 也不會失敗。|  
  
## 備註  
 擷取的識別項可以用來對指令碼執行緒執行控制方法的後續呼叫 \(例如 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 方法。  
  
 這個方法只能從非 Base 執行緒呼叫未使非基底 Callout 裝載物件或加入至 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 介面。  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)