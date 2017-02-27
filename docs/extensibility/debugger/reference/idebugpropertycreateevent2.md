---
title: "IDebugPropertyCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyCreateEvent2"
helpviewer_keywords: 
  - "IDebugPropertyCreateEvent2 介面"
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會傳送偵錯引擎 \(DE\) 給工作階段的偵錯專案經理 \(SDM\) 時，它會建立與特定文件相關聯的屬性。  
  
## 語法  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面來報告已經建立的屬性。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  如果 DE 已經建立了一個已載入或建立的指令碼相關聯的屬性，且這段指令碼必須出現在 IDE 中，則會實作這個介面。  
  
## 呼叫者的備忘稿  
 DE 建立，並將此事件物件傳送至已建立屬性的報告。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)連接偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugPropertyCreateEvent2`介面。  
  
|方法|描述|  
|--------|--------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|取得新的屬性。|  
  
## 備註  
 如果屬性具有特定的文件或與其相關聯的指令碼，DE 可以傳送這個事件給 SDM 使能更新**指令碼文件**視窗與文件的名稱。  SDM 會呼叫[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)與引數`guidDocument`擷取`VARIANT`包含[IUnknown](/visual-cpp/atl/iunknown)指標。  SDM 會呼叫[QueryInterface](/visual-cpp/atl/queryinterface)上擷取 this 指標[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面，用來更新**指令碼文件**視窗。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)