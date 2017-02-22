---
title: "IDebugProcessEx2 | Microsoft Docs"
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
  - "IDebugProcessEx2"
helpviewer_keywords: 
  - "IDebugProcessEx2 介面"
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會讓偵錯管理員 \(SDM\) 的通知，它會附加至或從處理序中斷連結處理序工作階段。  
  
## 語法  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者以相同的物件上實作這個介面[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面以：  
  
-   支援追蹤的工作階段連線到處理程序  
  
-   支援自動附加跨多個偵錯引擎  
  
 如果選擇自訂的連接埠提供者就可以實作這個介面。  
  
## 呼叫者的備忘稿  
  
-   SDM 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugProcess2`以取得這個介面的介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProcessEx2`。  
  
|方法|描述|  
|--------|--------|  
|[附加](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|通知處理序工作階段現在偵錯的處理程序。|  
|[中斷連結](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|通知處理序工作階段不會再偵錯的處理程序。|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|新增程式的偵錯引擎的清單的節點。|  
  
## 備註  
 這個介面是私用 SDM 和處理序之間。  
  
## 需求  
 標頭: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)