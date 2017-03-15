---
title: "刪除中斷點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "刪除的中斷點"
  - "偵錯 [偵錯 SDK]，請刪除中斷點"
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 刪除中斷點
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下說明刪除暫止中斷點時的處理程序：  
  
## 刪除程序  
 工作階段偵錯管理員 \(SDM\) 會呼叫 [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 方法以移除暫止中斷點和所有繫結的中斷點繫結自它。  
  
> [!NOTE]
>  單一繫結的中斷點也可以刪除呼叫 [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)