---
title: "IDebugEngineCreateEvent2 | Microsoft Docs"
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
  - "IDebugEngineCreateEvent2"
helpviewer_keywords: 
  - "IDebugEngineCreateEvent2 介面"
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

偵錯引擎 \(DE\) DE 的執行個體建立時，將這個介面傳送給工作階段的偵錯專案經理 \(SDM\)。  
  
## 語法  
  
```  
IDebugEngineCreateEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面，其正常作業的一部分。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件 \(使用 SDM `QueryInterface`方法來存取`IDebugEvent2`介面\)。  
  
## 呼叫者的備忘稿  
 DE 建立，並會傳送這個事件的物件，當 DE 具現化為止。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugEngineCreateEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|擷取的物件，表示新建立的偵錯引擎 \(DE\)。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)