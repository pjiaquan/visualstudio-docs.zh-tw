---
title: "IActiveScript::GetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptState"
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptState
擷取指令碼引擎的目前狀態。  這個方法只能從非 Base 執行緒呼叫未使非基底 Callout 裝載物件或加入至 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 介面。  
  
## 語法  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### 參數  
 `pss`  
 \[out\] 接收值的變數的位址。 [SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md) 列舉型別定義。  值指示指令碼引擎的目前狀態相關聯的執行緒。  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_POINTER` ，如果無效的指標被指定。  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)