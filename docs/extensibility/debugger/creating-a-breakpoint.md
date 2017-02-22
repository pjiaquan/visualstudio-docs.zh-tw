---
title: "建立的中斷點 | Microsoft Docs"
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
  - "建立的中斷點"
  - "偵錯 [偵錯 SDK]，請建立中斷點"
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 建立的中斷點
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下說明的程序建立中斷點。  
  
## 在中斷點建立的方法  
 載入該模組所需繫結中斷點時，工作階段偵錯管理員 \(SDM\) 會呼叫下列方法：  
  
1.  [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  **CanBind** 使用者尚未在 \[中斷點\] 視窗的中斷點時，才會呼叫。  
  
4.  [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)