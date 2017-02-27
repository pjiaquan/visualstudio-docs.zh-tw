---
title: "IDebugPortEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2"
helpviewer_keywords: 
  - "IDebugPortEx2 介面"
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPortEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會讓偵錯管理員 」 \(SDM\) 控制項，程式和連接埠上執行的處理序工作階段。  
  
## 語法  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者實作的同一個物件上實作這個介面[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)。  
  
## 呼叫者的備忘稿  
 SDM 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugPort2`以取得這個介面的介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugPortEx2`。  
  
|方法|描述|  
|--------|--------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|啟動可執行檔。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|繼續執行處理程序。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|決定是否可以終止處理程序。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|結束處理程序。|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|取得連接埠的處理序 ID。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|取得與程式節點相關聯的程式。|  
  
## 備註  
 這個介面是 SDM 和自訂的通訊埠供應商之間通常私用的。  
  
 偵錯引擎 \(DE\) 如有需要，可以查看這個介面[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面傳遞至[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) ，並使用[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)以啟動程式。  這不是必要的不過，並將 DE 辦得到它所要執行以啟動要求的程式。  
  
## 需求  
 標頭: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)