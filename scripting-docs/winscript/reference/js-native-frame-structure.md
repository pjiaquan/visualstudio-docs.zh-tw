---
title: "JS_NATIVE_FRAME 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JS_NATIVE_FRAME 結構
代表堆疊框架。  
  
## 語法  
  
```  
typedef struct {  
    UINT64 InstructionOffset;  
    UINT64 ReturnOffset;  
    UINT64 FrameOffset;  
    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## Members  
 `InstructionOffset`  
 指令指標。  
  
 `ReturnOffset`  
 傳回位址。  
  
 `FrameOffset`  
 框架指標。  
  
 `StackOffset`  
 堆疊指標。  
  
## 備註  
 `JS_NATIVE_FRAME` 建構是由 `IJsStackFrameEnumerator` 使用。  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)