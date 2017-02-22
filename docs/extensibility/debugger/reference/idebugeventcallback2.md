---
title: "IDebugEventCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2"
helpviewer_keywords: 
  - "IDebugEventCallback2"
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此介面用於偵錯引擎 \(DE\) 傳送給工作階段的偵錯專案經理 \(SDM\) 的偵錯事件。  
  
## 語法  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## 實作器注意事項  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]實作這個介面來接收來自偵錯引擎的事件。  
  
## 呼叫者的備忘稿  
 偵錯引擎通常這個介面時，會收到 SDM 會呼叫[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)， [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)，或[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  偵錯引擎將事件傳送至 SDM 藉由呼叫[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugEventCallback2`。  
  
|方法|描述|  
|--------|--------|  
|[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|傳送通知的偵錯 SDM 的事件。|  
  
## 備註  
 雖然[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)和[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)指定他們所採取`IDebugEventCallback2`介面，這並不大小寫，而且介面指標，就能為 null 值。  偵錯引擎必須改用`IDebugEventCallback2`介面收到的呼叫[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)， [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)，或[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
 如果封裝實作[IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md)在 managed 程式碼，強烈建議您， <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A>傳遞至不同的介面上被叫用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)