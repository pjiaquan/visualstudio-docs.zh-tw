---
title: "中斷點相關的方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，中斷點方法"
  - "方法的中斷點"
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 中斷點相關的方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯引擎 \(DE\) 必須支援中斷點的設定。  Visual Studio 的偵錯支援下列類型的中斷點：  
  
-   繫結  
  
     要求透過 UI，並成功地繫結至指定的程式碼的位置  
  
-   暫止  
  
     透過 UI，但是尚未結合到實際的指示要求  
  
## 討論  
 比方說，指示不尚未載入時，就會發生暫止中斷點。  當程式碼載入時，暫止中斷點請試著將繫結至程式碼的相關位置，也就是，程式碼中插入分行符號的指示。  事件都傳送到工作階段偵錯管理員 \(SDM\) 中，以指示成功的繫結，或是通知發生繫結錯誤。  
  
 暫止中斷點也管理自己的內部清單的相對應的繫結中斷點。  暫止中斷點在程式碼，就會造成許多中斷點的插入動作。  Visual Studio 的偵錯 UI 中顯示的樹狀檢視暫止中斷點，其對應的繫結中斷點。  
  
 建立和使用暫止中斷點需要實作 [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 方法，以及下列的方法 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 介面。  
  
|方法|描述|  
|--------|--------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|決定是否指定暫止中斷點可以繫結至程式碼的位置。|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|繫結指定的暫止中斷點至一或多個程式碼的位置。|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|取得暫止中斷點的狀態。|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|取得用來建立暫止中斷點的中斷點要求。|  
|[啟用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換暫止中斷點的啟用的狀態。|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|列舉所有繫結從暫止中斷點的中斷點。|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|列舉所造成的暫止中斷點的所有錯誤中斷點。|  
|[Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除擱置中的中斷點，並從其繫結的所有中斷點。|  
  
 若要列舉的繫結的中斷點和錯誤中斷點，您必須實作所有方法的 [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) 和 [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)。  
  
 暫止繫結至程式碼的中斷點位置必須實作下列 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 方法。  
  
|方法|描述|  
|--------|--------|  
|[GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)|取得含有中斷點的暫止中斷點。|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|取得繫結中斷點的狀態。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|取得說明中斷點的中斷點解析度。|  
|[啟用](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或停用中斷點。|  
|[Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除繫結的中斷點。|  
  
 解析度及要求資訊需要實作下列 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 方法。  
  
|方法|描述|  
|--------|--------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|取得中斷點的解析度所表示的型別。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|取得說明中斷點的中斷點解析資訊。|  
  
 在繫結期間可能發生之錯誤的解決方法需要有實作，下列 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 方法。  
  
|方法|描述|  
|--------|--------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|取得包含錯誤中斷點的暫止中斷點。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|取得描述錯誤中斷點中斷點錯誤解析。|  
  
 在繫結期間可能發生之錯誤的解決方式也會需要下列的方法 [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)。  
  
|方法|描述|  
|--------|--------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|取得中斷點的類型。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|取得中斷點的解析資訊。|  
  
 檢視在中斷點的原始程式碼會要求您實作的方法 [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 及 \(或\) 方法的 [IDebugStackFrame2::GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)。  
  
## 請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)