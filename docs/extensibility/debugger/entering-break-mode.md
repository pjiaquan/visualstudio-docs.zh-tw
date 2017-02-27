---
title: "進入中斷模式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中斷模式"
  - "偵錯 [偵錯 SDK]，請進入中斷模式"
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 進入中斷模式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下列將描述當遇到中斷點逐步執行函式、 執行中，有的資料指標的原始程式碼行或執行到中斷點之後，就會發生的處理程序。  
  
## 中斷模式處理程序  
  
1.  偵錯引擎 \(DE\) 傳送 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)，  [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)，或任何其他停止事件會造成 IDE 進入中斷模式。  
  
2.  SDM 從執行緒中，取得的呼叫堆疊資訊的如下所示：  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)  
  
    -   [IEnumDebugFrameInfo2::Next](../Topic/IEnumDebugFrameInfo2::Next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 以取得原始檔程式碼的資訊  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) 取得檔名  
  
    -   [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 以取得陳述式範圍  
  
    -   [IDebugStackFrame2::GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) 以取得記憶體資訊  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)