---
title: "IDebugPortEvents2 | Microsoft Docs"
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
  - "IDebugPortEvents2"
helpviewer_keywords: 
  - "IDebugPortEvents2 介面"
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會告知接聽程式 \(通常是工作階段偵錯管理員 \[SDM\] 或偵錯引擎\) 的處理程序和程式的建立與特定連接埠的解構。  這項資訊可用來提供處理序和連接埠上執行之程式的即時檢視。  
  
## 語法  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## 實作器注意事項  
 Visual Studio 通常會實作這個介面來接收通知程式建立和解構。  偵錯引擎也可以實作這個介面來接聽此連接埠的事件。  
  
## 呼叫者的備忘稿  
 所有[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面可以查詢<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面。  然後在<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A>方法`IDebugPortEvents2`中呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面，以取得<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面。  最後， <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>中的方法<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面則稱為 「 傳送到事件[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)方法。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugPortEvents2`。  
  
|方法|描述|  
|--------|--------|  
|[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)|傳送說明建立和解構的程序和連接埠上的應用程式的事件。|  
  
## 備註  
 `IDebugPortEvents2`也可供 SDM 偵錯已進行偵錯的處理序中執行的程式。  
  
 連接埠的事件會傳遞至 SDM 中，這個介面。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)