---
title: "BREAKREASON 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKREASON 列舉"
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# BREAKREASON 列舉
指出造成中斷。  
  
## 語法  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## Members  
  
|成員|描述|  
|--------|--------|  
|BREAKREASON\_STEP|語言引擎在執行模式下。|  
|BREAKREASON\_BREAKPOINT|語言引擎遇到一個明確的中斷點。|  
|BREAKREASON\_DEBUGGER\_BLOCK|語言引擎發生在另一個執行緒的偵錯工具區塊。|  
|BREAKREASON\_HOST\_INITIATED|主應用程式需要中斷。|  
|BREAKREASON\_LANGUAGE\_INITIATED|語言引擎要求中斷。|  
|BREAKREASON\_DEBUGGER\_HALT|偵錯工具 IDE 要求中斷。|  
|BREAKREASON\_ERROR|執行錯誤造成中斷。|  
|BREAKREASON\_JIT|產生由 JIT 偵錯開始。|  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)