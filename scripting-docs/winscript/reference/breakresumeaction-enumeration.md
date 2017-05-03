---
title: "BREAKRESUMEACTION 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKRESUMEACTION 列舉"
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKRESUMEACTION 列舉
描述從中斷點繼續執行的方式。  
  
## 語法  
  
```  
typedef enum tagBREAKRESUME_ACTION {    BREAKRESUMEACTION_ABORT,    BREAKRESUMEACTION_CONTINUE,    BREAKRESUMEACTION_STEP_INTO,    BREAKRESUMEACTION_STEP_OVER,    BREAKRESUMEACTION_STEP_OUT,    BREAKRESUMEACTION_IGNORE,    BREAKRESUMEACTION_STEP_DOCUMENT, } BREAKRESUMEACTION;  
```  
  
## Members  
  
|成員|描述|  
|--------|--------|  
|BREAKRESUMEACTION\_ABORT|中止應用程式。|  
|BREAKRESUMEACTION\_CONTINUE|繼續執行。|  
|BREAKRESUMEACTION\_STEP\_INTO|逐步執行程序。|  
|BREAKRESUMEACTION\_STEP\_OVER|不進入程序。|  
|BREAKRESUMEACTION\_STEP\_OUT|跳離目前的程序。|  
|BREAKRESUMEACTION\_IGNORE|在狀態下繼續執行。|  
|BREAKRESUMEACTION\_STEP\_DOCUMENT|繼續執行下一個文件。|  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)