---
title: "IDebugProcess2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2"
helpviewer_keywords: 
  - "IDebugProcess2 介面"
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示連接埠上執行的處理序。  如果連接埠本機連接埠，然後`IDebugProcess2`通常代表本機電腦上的實體處理程序。  
  
## 語法  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## 實作器注意事項  
 實作這個介面是由管理程式，作為一組自訂的通訊埠供應商。  藉由連接埠提供者，就必須實作這個介面。  
  
 偵錯引擎也實作這個介面支援啟動的程式，透過[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
## 呼叫者的備忘稿  
 主要工作階段偵錯管理員 \(SDM\) 會呼叫這個介面以互動與一群這項程序中所識別的程式。  
  
 呼叫[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)或[GetProcess](../Topic/IDebugPort2::GetProcess.md)以取得這個介面。  這個介面，也會傳回藉由呼叫`IDebugEngineLaunch2::LaunchSuspended`。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProcess2`。  
  
|方法|描述|  
|--------|--------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|取得處理序的描述。|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|列舉這個處理程序中所包含的程式。|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|取得標題、 好記的名稱或檔名的處理程序。|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|取得電腦伺服器執行此程序的執行個體。|  
|[結束](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|結束處理程序。|  
|[附加](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|將附加至處理序。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|決定是否 SDM 可以中斷與處理序。|  
|[中斷連結](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|中斷連結處理序與偵錯工具。|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|取得系統處理序識別項。|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|取得這個處理序中的全域唯一識別項。|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> \[取代\]|取得工作階段，偵錯的處理程序的名稱。<br /><br /> \[已被取代。  應該永遠傳回`E_NOTIMPL`。\]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|列舉處理序中執行的執行緒。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|要求在此程序停止執行程式碼的下一個程式。|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|取得連接埠上執行此程序。|  
  
## 備註  
 `IDebugProcess2`包含一或多個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../Topic/IDebugPort2::GetProcess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)