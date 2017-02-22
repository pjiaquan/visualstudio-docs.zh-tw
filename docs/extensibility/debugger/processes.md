---
title: "處理序 | Microsoft Docs"
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
  - "偵錯 [偵錯 SDK]，處理"
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 處理序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯工具的架構的角度來看**處理程序**：  
  
-   是一組程式的容器。  很接近類似 Windows 程序，也就是一組執行緒的容器。  
  
-   可以依名稱、 識別項或實體的識別項識別自己。  
  
-   可以列舉所有執行中的程式 \(和其執行緒\)。  
  
-   可以描述本身、 連接埠正執行，以及包含它的電腦。  
  
-   可以建立一個或多個程式終止的任何程式，它會建立，或導致程式停止。  
  
-   由[IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)介面，當處理序啟動時建立。  處理序已啟動任一個工作階段偵錯管理員 \(SDM\) 或[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
 偵錯封裝可以附加至處理序偵錯引擎 \(DE\) 藉由呼叫[附加](../../extensibility/debugger/reference/idebugprocess2-attach.md)。  這表示 DE 附加所有可能的程式，它可以處理程序中執行。  比方說，如果 common language runtime DE 附加至處理序，其會連接只執行 managed 程式碼中的程式。  
  
## 請參閱  
 [Programs](../../extensibility/debugger/programs.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)   
 [偵錯封裝](../../extensibility/debugger/debug-package.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [附加](../../extensibility/debugger/reference/idebugprocess2-attach.md)