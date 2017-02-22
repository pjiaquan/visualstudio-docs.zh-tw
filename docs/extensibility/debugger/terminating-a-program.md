---
title: "結束程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式終止事件"
  - "偵錯 [偵錯 SDK]，結束程式"
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 結束程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下是程式的單一，而且其中一個執行緒終止的描述。  
  
## 終止處理程序  
  
1.  DE 傳送 [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) 與有效的 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)。  
  
2.  DE 傳送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 與有效的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)。  
  
 IDE 會進入設計模式中。  偵錯引擎或執行階段環境呼叫 [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) ，移除從連接埠的程式。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)