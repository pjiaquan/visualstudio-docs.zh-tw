---
title: "APPBREAKFLAGS 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "APPBREAKFLAGS 的常數"
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# APPBREAKFLAGS 列舉
表示目前偵錯應用程式和執行緒的狀態。  
  
## 語法  
  
```cpp  
enum enum_APPBREAKFLAGS  
{  
APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,  
APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,  
APPBREAKFLAG_STEP= 0x00010000,  
APPBREAKFLAG_NESTED= 0x00020000,  
APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,  
APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,  
APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,  
APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,  
APPBREAKFLAG_IN_BREAKPOINT= 0x80000000  
};  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|APPBREAKFLAG\_DEBUGGER\_BLOCK|0x00000001|語言引擎緊接在與 BREAKREASON\_DEBUGGER\_BLOCK 的所有執行緒均應中斷。|  
|APPBREAKFLAG\_DEBUGGER\_HALT|0x00000002|語言引擎應該立即中斷與 BREAKREASON\_DEBUGGER\_HALT。|  
|APPBREAKFLAG\_STEP|0x00010000|語言引擎緊接在與 BREAKREASON\_STEP 逐步執行的執行緒應中斷。|  
|APPBREAKFLAG\_NESTED|0x00020000|應用程式在中斷點的巢狀執行。|  
|APPBREAKFLAG\_STEPTYPE\_SOURCE|0x00000000|偵錯工具逐步執行在來源層級。|  
|APPBREAKFLAG\_STEPTYPE\_BYTECODE|0x00100000|偵錯工具進入位元組程式碼層級。|  
|APPBREAKFLAG\_STEPTYPE\_MACHINE|0x00200000|偵錯工具逐步執行在電腦層級。|  
|APPBREAKFLAG\_STEPTYPE\_MASK|0x00F00000|分解的步驟類型遮罩。|  
|APPBREAKFLAG\_IN\_BREAKPOINT|0x80000000|中斷點的過程中。|  
  
## 備註  
 某些旗標指定語言引擎應中斷在下一個機會，，而其他旗標指定偵錯工具逐步執行的方式。  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)