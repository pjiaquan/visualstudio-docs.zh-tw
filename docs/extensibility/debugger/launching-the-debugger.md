---
title: "啟動偵錯工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK]，啟動偵錯工具"
  - "偵錯工具 [偵錯 SDK] 啟動"
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 啟動偵錯工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

啟動偵錯工具需要傳送正確的方法和事件及其適當的屬性順序。  
  
## 序列的方法和事件  
  
1.  工作階段偵錯管理員 \(SDM\) 選擇，會呼叫**偵錯** \] 功能表中，然後再選擇 **開始**。  如需詳細資訊，請參閱 [啟動程式](../../extensibility/debugger/launching-a-program.md)。  
  
2.  SDM 呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。  
  
3.  根據 \[偵錯引擎 \(DE\) 處理序模型中， `IDebugProgramNodeAttach2::OnAttach`方法會傳回下列方法之一，這麼做會決定接下來呢。  
  
     如果`S_FALSE`傳回時，偵錯引擎 \(DE\) 是要載入的虛擬機器的程序。  
  
     \-或\-  
  
     如果`S_OK`會傳回 DE 是載入同處理序的 SDM。  SDM 會接著執行下列工作：  
  
    1.  呼叫[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)以取得引擎的 DE 的資訊。  
  
    2.  會同時建立 DE。  
  
    3.  呼叫 [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
4.  DE 傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)與 SDM 到`EVENT_SYNC`屬性。  
  
5.  DE 傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)與 SDM 到`EVENT_SYNC`屬性。  
  
6.  DE 傳送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)與 SDM 到`EVENT_SYNC`屬性。  
  
7.  DE 傳送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)與 SDM 到`EVENT_SYNC`屬性。  
  
8.  DE 傳送[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)與 SDM 到`EVENT_SYNC`屬性。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)   
 [啟動程式](../../extensibility/debugger/launching-a-program.md)