---
title: "程式控制權 | Microsoft Docs"
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
  - "偵錯 [偵錯 SDK]，控制項的執行"
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 程式控制權
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 的偵錯時，所有下列的逐步執行，並繼續常式發生在程式層級：  
  
-   設定下一個陳述式，也就設定為在特定的圖文框的環境中執行的下一個指令的電腦  
  
-   結束逐步執行模式下執行時，也就繼續進行  
  
-   逐步執行至下一個指令  
  
-   繼續目前的逐步執行模式  
  
-   暫止的執行緒所包含的程式  
  
-   繼續執行緒所包含的程式  
  
> [!NOTE]
>  檢視呼叫堆疊是在執行緒層級上實作。  若要檢視執行緒的呼叫堆疊時，請列舉畫面資訊，您必須實作所有方法的 [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 介面。  
  
## 程式控制權的方法  
 下表顯示的方法 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ，就必須實作最少功能的偵錯引擎 \(DE\) 和執行控制項。  
  
|方法|描述|  
|--------|--------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|會繼續執行所有的執行緒所包含的程式，從停止的狀態。  執行控制項的必要項。|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|會繼續執行所有的執行緒所包含的程式，從停止的狀態。  執行控制項的必要項。|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|在指定的執行緒上執行的步驟。  會繼續執行其他程式所包含的所有執行緒。  執行控制項的必要項。|  
  
 若為多執行緒程式，您也必須實作 [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 方法，所有方法的 [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) 介面。  
  
## 請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)