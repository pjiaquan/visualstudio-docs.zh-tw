---
title: "IDebugEntryPointEvent2 | Microsoft Docs"
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
  - "IDebugEntryPointEvent2"
helpviewer_keywords: 
  - "IDebugEntryPointEvent2 介面"
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

偵錯引擎 \(DE\) 執行使用者程式碼的第一個指令程式時，將這個介面傳送給工作階段的偵錯專案經理 \(SDM\)。  
  
## 語法  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面，其正常作業的一部分。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 建立，並會傳送這個事件的物件，當偵錯程式已載入，並準備好執行使用者程式碼的第一個指令。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 備註  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)執行第一個指令程式時，會傳送。  例如， `IDebugEntryPoint2`程式即將執行使用者的連線時立即傳送`main`函式。  
  
 何時會傳送 DE `IDebugEntryPointEvent2`，目前的程式碼位置應該位於第一個指令的使用者程式碼，像是`main`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)