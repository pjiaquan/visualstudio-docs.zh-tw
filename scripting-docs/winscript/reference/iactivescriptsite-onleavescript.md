---
title: "IActiveScriptSite::OnLeaveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnLeaveScript"
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnLeaveScript
告知主應用程式指令碼引擎從執行指令碼傳回。  
  
## 語法  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## 傳回值  
 如果成功，會傳回 `S_OK`。  
  
## 備註  
 指令碼引擎必須在傳回控制項之前呼叫這個方法會取得輸入指令碼引擎的呼叫的應用程式。  例如，如果指令碼呼叫，接著引發指令碼引擎處理之事件的物件，指令碼引擎必須在執行事件 [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) 之前呼叫方法，而且必須在執行事件之後呼叫 `IActiveScriptSite::OnLeaveScript` 後再傳回至引發事件的物件。  對這個方法的呼叫可以是巢狀結構。  為 `IActiveScriptSite::OnEnterScript` 的每一個呼叫中必須有對應的呼叫這個方法。  
  
## 請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)