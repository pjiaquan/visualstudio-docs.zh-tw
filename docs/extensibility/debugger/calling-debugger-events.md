---
title: "呼叫偵錯工具事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK] 事件"
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 呼叫偵錯工具事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在偵錯工作階段的事件會發生特定的順序。  
  
## 討論  
 若要瞭解模式的偵錯引擎 \(DE\) 和 「 工作階段偵錯管理員 」 \(SDM\) 之間的呼叫，以下代表在典型的偵錯工作階段中發生的事件呼叫的順序：  
  
1.  [附加及分離的程式](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [啟動偵錯工具](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [結束程式](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [建立中斷點](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [中斷點會繫結，或成為非結合](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [中斷點錯誤](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [方式來點擊中斷點](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [刪除中斷點](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [進入中斷模式](../../extensibility/debugger/entering-break-mode.md)  
  
10. [在中斷模式中逐步執行](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [在中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [例外狀況處理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## 請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)