---
title: "在中斷模式中逐步執行 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中斷模式中，逐步執行"
  - "逐步執行，在中斷模式"
  - "偵錯 [偵錯 SDK]，請在中斷模式中逐步執行"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 在中斷模式中逐步執行
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下說明偵錯工具處於中斷模式，並必須逐步執行程式碼時，就會發生的處理程序：  
  
## 逐步執行的處理程序  
  
1.  呼叫 [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) 與 [STEPKIND](../../extensibility/debugger/reference/stepkind.md) 和 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 引數，若要執行的步驟。  
  
2.  完成此步驟時，傳送 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 以停止事件。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)