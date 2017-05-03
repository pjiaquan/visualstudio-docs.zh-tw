---
title: "IActiveScript::GetScriptThreadState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadState"
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadState
擷取指令碼執行緒目前的狀態。  
  
## 語法  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### 參數  
 `stidThread`  
 \[in\] 這個狀態所需的執行緒下列特殊執行緒識別項的識別項或其中一項:  
  
|值|意義|  
|-------|--------|  
|SCRIPTTHREADID\_BASE|基本的執行緒;也就是指令碼引擎執行個體化的執行緒。|  
|SCRIPTTHREADID\_CURRENT|目前正在執行的執行緒。|  
  
 `pstsState`  
 \[out\] 接收表示執行緒的狀態變數的位址。  狀態由 [SCRIPTTHREADSTATE 列舉](../../winscript/reference/scriptthreadstate-enumeration.md) 列舉型別中定義的其中一個具名常數值的運算式。  如果這個參數不會識別目前的執行緒，則狀態可能會隨時變更。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\)。|  
  
## 備註  
 這個方法只能從非 Base 執行緒呼叫未使非基底 Callout 裝載物件或加入至 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 介面。  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)