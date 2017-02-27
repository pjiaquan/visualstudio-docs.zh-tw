---
title: "附加和中斷連結至程式 | Microsoft Docs"
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
  - "偵錯引擎，中斷連結程式"
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 附加和中斷連結至程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

附加偵錯工具需要傳送正確的方法和事件，以適當的屬性順序。  
  
## 方法和事件的順序  
  
1.  工作階段偵錯管理員 \(SDM\) 會呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。  
  
     根據 \[偵錯引擎 \(DE\) 處理序模型中， `IDebugProgramNodeAttach2::OnAttach`方法會傳回下列方法之一，這麼做會決定接下來呢。  
  
     如果`S_FALSE`傳回時，偵錯引擎已成功地附加到程式。  否則， [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)會呼叫方法來完成附加程序。  
  
     如果`S_OK`會傳回 DE 已載入相同 SDM 的處理序中。  SDM 會執行下列工作：  
  
    1.  呼叫[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)以取得引擎的 DE 的資訊。  
  
    2.  會同時建立 DE。  
  
    3.  呼叫 [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
2.  DE 傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)與 SDM 到`EVENT_SYNC`屬性。  
  
3.  DE 傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)與 SDM 到`EVENT_SYNC`屬性。  
  
4.  DE 傳送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)與 SDM 到`EVENT_SYNC_STOP`屬性。  
  
 中斷連結的程式是一種簡單、 兩個步驟，如下所示：  
  
1.  SDM 呼叫[中斷連結](../../extensibility/debugger/reference/idebugprogram2-detach.md)。  
  
2.  DE 傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)