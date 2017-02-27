---
title: "在啟動後附加 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯引擎，附加至程式"
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 在啟動後附加
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在啟動程式後，偵錯工作階段已附加偵錯引擎 \(DE\) 給該程式。  
  
## 設計決策  
 因為通訊很容易在共用的位址空間內，您必須決定是否合理多個以利於進行偵錯工作階段之間的 DE 或 DE 與程式之間的通訊。  選擇下列兩者之一：  
  
-   如果程式能更有意義，以利於進行偵錯工作階段 」 與 「 DE 之間的通訊時，偵錯工作階段就會同時建立 DE 檔案，並詢問 DE 附加至程式中。  這會使偵錯工作階段和 DE 一起一個地址空間，以及執行階段環境和程式一起放在另一個。  
  
-   如果程式能更有意義，以幫助 DE 與程式之間的通訊時，執行階段環境會同時建立 DE。  這會使一個地址空間中的 SDM DE、 執行階段環境和程式一起放在另一個。  這是典型的實作與執行指令碼的語言直譯器搭配 DE。  
  
    > [!NOTE]
    >  DE 附加至該程式的方式是實作相依性。  DE 與程式之間的通訊也是實作相依性。  
  
## 實作  
 以程式設計的方式，當工作階段偵錯管理員 \(SDM\) 第一次收到[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ，表示要啟動程式的物件，它會呼叫[附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)方法，將它傳遞[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)物件，也就是稍後用來將偵錯事件傳遞回 SDM。  然後，`IDebugProgram2::Attach` 方法會呼叫 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。  如需有關如何接收 SDM `IDebugProgram2`介面，請參閱[通知連接埠](../../extensibility/debugger/notifying-the-port.md)。  
  
 如果您是在相同的位址空間，以進行偵錯，通常是因為 DE 屬於執行指令碼解譯器程式執行時所需`IDebugProgramNodeAttach2::OnAttach`方法傳回`S_FALSE`，表示它完成附加的處理程序。  
  
 如果相反地，DE 會在位址空間的 SDM， `IDebugProgramNodeAttach2::OnAttach`方法傳回`S_OK`或[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面的實作不完全在[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)進行偵錯的程式相關聯的物件。  如此一來， [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)最後會呼叫方法來完成附加作業。  
  
 在後者的情況下，您必須呼叫[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)上的方法`IDebugProgram2`物件傳遞至`IDebugEngine2::Attach`方法、 存放區`GUID`在本機的程式中的物件，並傳回這`GUID`時`IDebugProgram2::GetProgramId`隨後在此物件上呼叫方法。  `GUID`用來唯一識別各種偵錯元件之間的程式。  
  
 請注意，如果是`IDebugProgramNodeAttach2::OnAttach`方法傳回`S_FALSE`、 `GUID`程式所傳遞到該方法，而且很`IDebugProgramNodeAttach2::OnAttach` ，設定方法`GUID`上本機程式物件。  
  
 DE 現在已連接到程式，且準備好要傳送任何啟動事件。  
  
## 請參閱  
 [直接附加程式](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [通知連接埠](../../extensibility/debugger/notifying-the-port.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)