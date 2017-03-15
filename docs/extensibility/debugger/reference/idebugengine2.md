---
title: "IDebugEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2"
helpviewer_keywords: 
  - "IDebugEngine2 介面"
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示偵錯引擎 \(DE\)。  它用來管理各方面的偵錯工作階段中，從建立中斷點，以設定及清除的例外狀況。  
  
## 語法  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## 實作器注意事項  
 實作這個介面是由自訂的 DE 管理偵錯的程式。  必須由 DE 實作這個介面。  
  
## 呼叫者的備忘稿  
 工作階段偵錯管理員 \(SDM\) 來管理偵錯工作階段，包括管理例外狀況、 建立中斷點，以及回應 DE 所傳送的同步事件會呼叫這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugEngine2`。  
  
|方法|描述|  
|--------|--------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|建立將 DE 偵錯的所有程式的列舉值。|  
|[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)|將 DE 附加至程式。|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|建立 DE 暫止中斷點。|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|指定 DE 應如何處理指定的例外狀況。|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|移除指定的例外狀況，因此不能再由偵錯引擎。|  
|[RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md)|IDE 已經設定為特定的執行階段架構或語言的例外清單中移除。|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|取得 DE 的 GUID。|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|通知的 DE，指出指定的程式已經終止不規則且 DE 應清除該程式的所有參考，並傳送程式損毀的事件。|  
|[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)|呼叫以指示同步的偵錯事件，先前傳送給 SDM，DE 已接收並處理 SDM。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|設定 DE 的地區設定。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|正在使用的 DE 目前設定的登錄根目錄。|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|設定度量單位。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|這是由偵錯的所有程式都停止執行其中一項他們的執行緒嘗試執行的下一次的要求。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)