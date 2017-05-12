---
title: "SCRIPTSTATE 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTSTATE 列舉"
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTSTATE 列舉
指定一個指令碼引擎的狀態。  [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) 、 [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) 和 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 方法使用這個列舉型別 \(Enumeration\)。  
  
## 語法  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## 列舉值  
  
|||  
|-|-|  
|SCRIPTSTATE\_UNINITIALIZED|使用 `IPersist*` 介面和 [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) ，指令碼，建立，但尚未初始化。|  
|SCRIPTSTATE\_INITIALIZED|指令碼已經初始化，但是，執行 \(連接至其他物件或接收事件\) 也不會執行任何程式碼。  程式碼可以執行查詢以呼叫 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) 方法。|  
|SCRIPTSTATE\_STARTED|指令碼可執行程式碼，但是，接收 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法加入物件的事件。|  
|SCRIPTSTATE\_CONNECTED|指令碼會接收的事件已載入及連接。|  
|SCRIPTSTATE\_DISCONNECTED|指令碼載入和具有執行階段執行狀態，不過，從接收的事件暫時中斷連接。|  
|SCRIPTSTATE\_CLOSED|指令碼隨即關閉。  指令碼引擎無法再運作並傳回大部分方法時發生錯誤。|  
  
## 請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)