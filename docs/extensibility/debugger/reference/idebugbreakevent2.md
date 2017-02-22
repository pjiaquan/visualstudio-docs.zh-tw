---
title: "IDebugBreakEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakEvent2"
helpviewer_keywords: 
  - "IDebugBreakEvent2 介面"
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會告知偵錯叢集 \(SDM\) 非同步的中斷已順利完成。  
  
## 語法  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面以支援使用者符號在程式中。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件 \(使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面\)。  
  
## 呼叫者的備忘稿  
 SDM 呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)時使用者已要求正在進行偵錯，來暫停程式。  如果程式已順利暫停，會將傳送 DE `IDebugBreakEvent2`事件。  藉由傳送這個事件時[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，由 SDM 提供的回呼函式。  
  
## 備註  
 比方說，使用者可以選取**中斷所有** 命令 **偵錯**破壞程式正在執行一個無限迴圈的功能表。  SDM 會告知程式停止藉由呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)。  DE 傳送`IDebugBreakEvent2`最後停止程式。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)