---
title: "SCRIPTTHREADSTATE 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADSTATE 列舉"
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTTHREADSTATE 列舉
在一個指令碼引擎指定執行緒的狀態。  這個列舉是由 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) 方法所使用。  
  
## 語法  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## 列舉值  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE\_NOTINSCRIPT|指定執行緒未指定指令化事件服務，目前處理序正執行的指令碼、文字或無法執行指令碼巨集。|  
|SCRIPTTHREADSTATE\_RUNNING|指定的執行緒為指令化事件服務，有效地管理立即執行指令碼的文字或執行指令碼巨集。|  
  
## 請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)