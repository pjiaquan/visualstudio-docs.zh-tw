---
title: "IDebugProcessDestroyEvent2 | Microsoft Docs"
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
  - "IDebugProcessDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProcessDestroyEvent2"
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

處理程序已終止、 不規則，結束或已中斷連結時，會傳送這個介面。  
  
## 語法  
  
```  
IDebugProcessDestroyEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 或自訂的連接埠提供者實作這個介面來報告處理程序已終止。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 或自訂的連接埠提供者會建立，並傳送這個事件物件，來報告處理程序終止。  DE 傳送這個事件使用[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)連接偵錯程式時，會將 SDM 所提供的回呼函式。  自訂的連接埠提供者會傳送這個事件使用[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)介面。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)