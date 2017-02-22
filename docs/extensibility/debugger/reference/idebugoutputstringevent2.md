---
title: "IDebugOutputStringEvent2 | Microsoft Docs"
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
  - "IDebugOutputStringEvent2"
helpviewer_keywords: 
  - "IDebugOutputStringEvent2 介面"
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面是由偵錯引擎 \(DE\) 中，給工作階段的偵錯專案經理 \(SDM\) 傳送到輸出字串。  
  
## 語法  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面來傳送字串到**輸出**在 ide 的視窗。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 建立並傳送這個事件物件，傳送字串到**輸出**視窗。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)連接偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugOutputStringEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetString](../Topic/IDebugOutputStringEvent2::GetString.md)|取得可顯示的訊息。|  
  
## 備註  
 比方說，在 unmanaged 程式碼，來輸出字串只能起始時進行偵錯的程式會將字串傳送到 Win32 `OutputDebugString`函式。  這個字串 DE 攔截，並傳送給與 SDM `IDebugOutputStringEvent2`事件。  
  
 使用[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)需要使用者回應的訊息。  
  
 使用[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)傳送錯誤訊息，而無須回應。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)