---
title: "支援的事件類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK]，支援事件"
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 支援的事件類型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 的偵錯目前支援下列的事件類型：  
  
-   非同步事件  
  
     通知偵錯叢集 \(SDM\) 與應用程式進行偵錯的狀態會變更 IDE。  SDM 和 IDE 的休閒處理這些事件。  若要偵錯引擎 \(DE\) 會不傳送任何回應，一旦處理其事件。  [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)和[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)介面都是非同步事件的範例。  
  
-   同步事件  
  
     告知 SDM 和 IDE 所偵錯應用程式的狀態會變更。  這些事件並非同步事件的唯一差異在於回覆會傳送的[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)方法。  
  
     傳送同步事件是很有用，如果您需要您 DE 繼續處理後，IDE 會接收並處理事件。  
  
-   同步停止事件，或停止事件  
  
     通知已停止執行程式碼進行偵錯應用程式的 SDM 與 IDE。  當您傳送停止事件的方法[事件](../../extensibility/debugger/reference/idebugeventcallback2-event.md)、 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)參數是必要的。  停止事件，會不斷地延續呼叫下列方法之一：  
  
    -   [執行](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [逐步執行](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [繼續](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     介面[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)是停止事件的範例。  
  
    > [!NOTE]
    >  不支援非同步停止事件。  它會發生錯誤就會傳送非同步停止事件。  
  
## 討論  
 事件的實際實作取決於您 DE 的設計。  傳送每個事件的型別取決於它的屬性，當您設計 DE 設定。  例如，一個 DE 可能會傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)為非同步事件，而另一個可能會以停止事件傳送。  
  
 下表會指定哪一個程式，並且執行緒參數都是必要的事件，以及事件類型。  任何事件可以是同步的。  沒有事件必須同步。  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md)介面是必要的所有事件。  
  
|事件|IDebugProgram2|IDebugThread2|停止事件|  
|--------|--------------------|-------------------|----------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|必要項|必要項|是|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|必要項|必要項|是|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|必要項|必要項|否|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|不允許。|不允許。|否|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|不允許。|不允許。|否|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|必要項|必要項|是|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|允許，但非必要|允許，但非必要|可以是|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|必要項|必要項|是|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|允許，但非必要|允許，但非必要|可以是|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|必要項|必要項|是|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|必要項|必要項|是|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|允許，但非必要|允許，但非必要|可以是|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|必要項|允許，但非必要|否|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|必要項|允許，但非必要|否|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|必要項|允許，但非必要|否|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|必要項|允許，但非必要|否|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|必要項|允許，但非必要|否|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|允許，但非必要|允許，但非必要|否|  
|IDebugStopCompleteEvent2|必要項|必要項|是|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|必要項|必要項|是|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|必要項|必要項|否|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|必要項|必要項|否|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|允許，但非必要|允許，但非必要|否|  
  
## 請參閱  
 [傳送事件](../../extensibility/debugger/sending-events.md)