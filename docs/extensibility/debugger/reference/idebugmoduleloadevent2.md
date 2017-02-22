---
title: "IDebugModuleLoadEvent2 | Microsoft Docs"
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
  - "IDebugModuleLoadEvent2"
helpviewer_keywords: 
  - "IDebugModuleLoadEvent2 介面"
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModuleLoadEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會傳送偵錯引擎 \(DE\) 給工作階段的偵錯專案經理 \(SDM\) 載入或卸載模組時。  
  
## 語法  
  
```  
IDebugModuleLoadEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 報表的模組已經載入或卸載這個介面實作為 DE。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 建立，並將此事件物件傳送到報表模組已經載入或卸載。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)連接偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugModuleLoadEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|取得模組正在載入或卸載。|  
  
## 備註  
 Visual Studio 會利用這個事件來讓**模組**最新的視窗。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)