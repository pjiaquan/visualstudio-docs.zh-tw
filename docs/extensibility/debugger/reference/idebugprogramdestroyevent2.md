---
title: "IDebugProgramDestroyEvent2 | Microsoft Docs"
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
  - "IDebugProgramDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProgramDestroyEvent2"
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會傳送偵錯引擎 \(DE\) 給工作階段的偵錯專案經理 \(SDM\) 時在程式執行到完成為止。  
  
## 語法  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 或自訂的連接埠提供者實作這個介面來報告某個程式已經終止，而且也不再適用於偵錯。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 或自訂的連接埠提供者會建立，並傳送報告程式的終止此事件物件。  DE 傳送這個事件使用[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，會將 SDM 所提供的回呼函式。  自訂的連接埠提供者會傳送這個事件使用[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProgramDestroyEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md)|取得程式的結束代碼。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)