---
title: "IActiveScriptSite::OnStateChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnStateChange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnStateChange"
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSite::OnStateChange
告知主應用程式指令碼引擎已變更狀態。  
  
## 語法  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### 參數  
 `ssScriptState`  
 \[in\] 數值則表示新指令碼的狀態。  如需狀態的描述參閱 [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) 方法。  
  
## 傳回值  
 如果成功，會傳回 `S_OK`。  
  
## 請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)