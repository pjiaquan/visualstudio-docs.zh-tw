---
title: "IActiveScriptSite::OnEnterScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnEnterScript"
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnEnterScript
告知主應用程式指令碼引擎開始執行指令碼。  
  
## 語法  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## 傳回值  
 如果成功，會傳回 `S_OK`。  
  
## 備註  
 指令碼引擎必須在每個項目或重新進入的這個方法加入至指令碼引擎中。  例如，如果指令碼呼叫，接著引發指令碼引擎處理之事件的物件，指令碼引擎必須在執行事件之前呼叫 `IActiveScriptSite::OnEnterScript` ，且必須呼叫方法 [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) 在執行事件之後，但在傳回之前加入引發事件的物件。  對這個方法的呼叫可以是巢狀結構。  對這個方法的每一個呼叫中必須有對應的呼叫。 `IActiveScriptSite::OnLeaveScript`。  
  
## 請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)