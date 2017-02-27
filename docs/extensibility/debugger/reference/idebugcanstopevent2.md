---
title: "IDebugCanStopEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2 介面"
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面用來詢問是否要停止目前的程式碼位置的 「 工作階段偵錯管理員 」 \(SDM\)。  
  
## 語法  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面以支援逐步執行程式碼。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件 \(使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面\)。  
  
 這個介面的實作必須告知 SDM 呼叫[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)偵錯引擎。  比方說，這可以張貼到偵錯引擎的訊息處理執行緒的訊息或無法保存至偵錯引擎實作這個介面的物件，並將其回呼至偵錯引擎使用傳遞至旗標`IDebugCanStopEvent2::CanStop`。  
  
## 呼叫者的備忘稿  
 DE 可以傳送這個方法 DE 將被要求繼續執行，以及 DE 每次逐步進行程式碼。  藉由傳送這個事件時[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，由 SDM 提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugCanStopEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)|取得這個事件的原因。|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|指定應該要在這個事件 \(及傳送事件描述停止的原因\) 的位置停止或繼續執行，只是偵錯的程式。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|取得描述這個事件的位置的文件內容。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|取得程式碼內容說明這個事件的位置。|  
  
## 備註  
 如果使用者逐步執行函式和 DE 尋找任何偵錯資訊或偵錯資訊存在，但 DE 不知道如果該位置會顯示原始程式碼，DE 就會傳送這個介面。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)