---
title: "IDebugExceptionEvent2 | Microsoft Docs"
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
  - "IDebugExceptionEvent2"
helpviewer_keywords: 
  - "IDebugExceptionEvent2 介面"
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

目前正在執行的程式中擲回例外狀況時，偵錯引擎 \(DE\) 給工作階段的偵錯專案經理 \(SDM\) 傳送這個介面。  
  
## 語法  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面來進行偵錯程式中發生例外狀況的報告。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 建立，並會傳送這個事件物件，來報告例外狀況。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugExceptionEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetException](../Topic/IDebugExceptionEvent2::GetException.md)|取得有關例外狀況引發這個事件的詳細的資訊。|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|取得擲回例外狀況引發這個事件之人們可讀取描述。|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|判斷偵錯引擎 \(DE\) 支援將此例外狀況傳遞給偵錯時繼續執行程式的選項。|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|指定的例外狀況應該傳遞給正在偵錯程式時則繼續執行，或如果應該捨棄例外狀況。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 備註  
 在傳送之前的事件，DE 檢查是否這個例外狀況事件被指定已發生第一個或第二個可能的例外狀況之前呼叫[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)。  如果它已被指定為第一個出現的例外狀況中， `IDebugExceptionEvent2`事件傳送至 SDM。  如果沒有，則是讓應用程式有機會處理例外狀況。  如果出現沒有例外處理常式，而例外狀況被指定為第二個可能的例外狀況， `IDebugExceptionEvent2`事件傳送至 SDM。  否則，DE 會繼續執行程式，而作業系統或執行階段處理的例外狀況。  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)