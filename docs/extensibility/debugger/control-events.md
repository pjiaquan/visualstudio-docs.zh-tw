---
title: "控制項事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK] 事件"
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 控制項事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

控制您的程式執行期間，您必須傳送事件。  使用的所有事件傳送 [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) 介面，並具有屬性，必須實作 [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) 方法。  
  
## 其他方法  
 有些事件會需要額外的方法的實作，如下所示：  
  
-   傳送 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 介面初始化偵錯引擎 \(DE\) 時，要求您實作 [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) 方法。  
  
-   執行控制項需要有實作，這類的控制項事件，做為 [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) 和[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 介面。  **IDebugBreakEvent2** 只需要非同步中斷。  
  
-   逐步執行函式需要有實作，  [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 介面和方法。  
  
 衍生自中斷點的事件都需要實作 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)，  [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)，以及  [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 介面，以及 [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 和 [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 方法。  
  
 非同步運算式的評估會要求您實作 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 介面，其 [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[和 GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 方法。  
  
 同步事件都需要實作 [IDebugEngine2::ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) 方法。  
  
 針對您要寫入字串樣式輸出的引擎，您必須執行 [IDebugOutputStringEvent2::GetString](../Topic/IDebugOutputStringEvent2::GetString.md) 方法。  
  
## 請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)