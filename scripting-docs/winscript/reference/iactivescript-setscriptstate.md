---
title: "IActiveScript::SetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptState"
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::SetScriptState
將指令碼引擎至指定的狀態。  這個方法只能從非 Base 執行緒呼叫未使非基底 Callout 裝載物件或加入至 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 介面。  
  
## 語法  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### 參數  
 `ss`  
 \[in\] 設定指令碼引擎對給定的狀態。  可以是 [SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md) 列舉型別中定義的其中一個值。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_FAIL`|指令碼引擎不支援轉換回這個初始狀態。  主應用程式必須捨棄這個指令碼引擎，以及建立、初始化和載入新的指令碼引擎達到相同的效果。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\) 也不會失敗。|  
|`OLESCRIPT_S_PENDING`|方法已成功加入佇列，，但是這個狀態未變更。  發生狀態變更，則站台可以 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 便會呼叫方法。|  
|`S_FALSE`|方法會成功，但是，指令碼已處於特定狀態。|  
  
## 備註  
 如需指令碼引擎狀態的詳細資訊，請參閱 [Windows 指令碼引擎](../../winscript/windows-script-engines.md) 的指令碼引擎狀態\>一節。  
  
## 請參閱  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)