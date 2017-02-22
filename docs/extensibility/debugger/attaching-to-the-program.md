---
title: "附加至程式 | Microsoft Docs"
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
  - "偵錯引擎，附加至程式"
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 附加至程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您已使用適當的連接埠來登錄您的程式後，您必須將偵錯工具附加至您要偵錯的程式。  
  
## 選擇如何附加  
 有三種方法，此工作階段偵錯管理員 \(SDM\) 嘗試附加至正在偵錯的程式。  
  
1.  程式會啟動偵錯引擎，透過[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) \(解譯的語言，例如典型\) 的方法，SDM 會取得[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面從[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)要附加至該程式相關聯的物件。  如果可以取得 SDM `IDebugProgramNodeAttach2`介面，然後呼叫 SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。  `IDebugProgramNodeAttach2::OnAttach`方法傳回`S_OK`以指出沒有未附加到程式，且可以附加至程式進行其他嘗試。  
  
2.  如果可以取得 SDM [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)與要附加至 SDM 呼叫該程式的介面[附加](../../extensibility/debugger/reference/idebugprogramex2-attach.md)方法。  這種方法是一般由連接埠提供者從遠端啟動的程式。  
  
3.  如果程式無法連接到`IDebugProgramNodeAttach2::OnAttach`或`IDebugProgramEx2::Attach`方法，SDM 就會將這個偵錯引擎 \(如果尚未載入\) 載入藉由呼叫`CoCreateInstance`函式，然後呼叫[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  這種方法是在本機啟動連接埠提供者的程式。  
  
     您也可呼叫自訂的通訊埠供應商的`IDebugEngine2::Attach`中的自訂通訊埠供應商的實作方法`IDebugProgramEx2::Attach`方法。  通常這種情況下，自訂的連接埠提供者會啟動遠端機器上的偵錯引擎。  
  
 工作階段偵錯管理員 \(SDM\) 呼叫方法附件是[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  
  
 如果您要偵錯時，應用程式相同的處理序中執行您 DE，那麼您就必須實作下列的方法[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)：  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 後`IDebugEngine2::Attach`呼叫方法時，請遵循下列步驟的實作中`IDebugEngine2::Attach`方法：  
  
1.  傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM 事件物件。  如需詳細資訊，請參閱 [傳送事件](../../extensibility/debugger/sending-events.md)。  
  
2.  呼叫[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)上的方法[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)物件傳遞至`IDebugEngine2::Attach`方法。  
  
     這會傳回`GUID` ，用來識別程式。  `GUID`必須儲存在該物件代表 DE，程式在本機，而且它必須傳回何時`IDebugProgram2::GetProgramId`上呼叫方法`IDebugProgram2`介面。  
  
    > [!NOTE]
    >  如果您決定使用`IDebugProgramNodeAttach2`介面，該程式的`GUID`傳遞至`IDebugProgramNodeAttach2::OnAttach`方法。  這`GUID`用於程式的`GUID`所傳回的`IDebugProgram2::GetProgramId`方法。  
  
3.  傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件的物件，以通知 SDM 的局部`IDebugProgram2` DE 代表程式建立物件。  如需詳細資訊，請參閱 [傳送事件](../../extensibility/debugger/sending-events.md)。  
  
    > [!NOTE]
    >  這並不相同`IDebugProgram2`物件傳遞至`IDebugEngine2::Attach`方法。  先前傳遞`IDebugProgram2`物件的連接埠只辨認出來，而且是不同的物件。  
  
## 請參閱  
 [啟動為基礎的附件](../../extensibility/debugger/launch-based-attachment.md)   
 [傳送事件](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [附加](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)