---
title: "IDebugProgram3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3 介面"
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示一種程式，在處理程序中執行，並擴充[執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md) ，提供的執行緒資訊。  
  
## 語法  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 和自訂的連接埠提供者實作這個介面表示處理程序中的程式。  工作階段偵錯管理員 \(SDM\) 也會實作這個介面來提供資訊給[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)。  
  
## 呼叫者的備忘稿  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件會傳回這個介面的新程式。  此介面也做為參數的多個介面上的許多方法。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProgram3`。  
  
|方法|描述|  
|--------|--------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|執行程式。  執行緒會傳回給哪一個執行緒執行時檢視使用者的偵錯工具資訊。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 備註  
 程式已經在特定的執行階段架構中，執行，而 \[處理程序由一或多個程式所組成的執行緒容器。  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [下一步](../Topic/IEnumDebugPrograms2::Next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)