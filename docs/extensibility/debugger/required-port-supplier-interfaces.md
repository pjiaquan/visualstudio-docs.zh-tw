---
title: "必要的連接埠供應商介面 | Microsoft Docs"
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
  - "連接埠供應商所需的介面"
  - "偵錯 [偵錯 SDK]，連接埠的供應商"
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 必要的連接埠供應商介面
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

連接埠提供者必須實作[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面。       [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 連接埠提供者提供的連接埠，因為它也必須實作它們。  因此，它必須實作下列介面：  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     說明連接埠，並可以列舉所有連接埠上執行的處理程序。  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     提供啟動和結束連接埠上的處理序。  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     提供一種機制，在此連接埠，告知程式節點建立和解構的內容中執行的程式。  如需詳細資訊，請參閱 [程式節點](../../extensibility/debugger/program-nodes.md)。  
  
-   `IConnectionPointContainer`  
  
     提供的連接點[IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)。  
  
## 連接埠的供應商作業  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)接收器時收到告知程序，並建立及終結的連接埠的程式。  連接埠，才能傳送[IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md)建立處理程序時， [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)處理程序時損毀的連接埠。  也需要一個連接埠傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)程式建立時， [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)程式在連接埠上執行的處理序時被終結。  
  
 連接埠通常會傳送程式建立和終結以回應事件[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)和[RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)方法，分別。  
  
 因為連接埠可以啟動，並終止實體的處理程序和邏輯的程式，偵錯引擎也必須實作這些介面：  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     描述實體的程序。  至少必須實作下列方法：  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     提供方法來連接和分離本身的處理程序 SDM。  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     描述邏輯的程式。  至少必須實作下列方法：  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     提供如附加至這個程式的 SDM 的方式。  
  
## 請參閱  
 [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)