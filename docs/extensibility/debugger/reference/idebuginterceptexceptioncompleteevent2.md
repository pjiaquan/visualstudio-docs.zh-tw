---
title: "IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2"
helpviewer_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2"
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugInterceptExceptionCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會傳送偵錯引擎 \(DE\) 給工作階段的偵錯專案經理 \(SDM\) DE 完成後被攔截的事件處理。  
  
## 語法  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面來報告被攔截的例外狀況的處理已完成。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 建立，並會傳送這個事件物件，來報告完成的被攔截的例外狀況。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 方法 Vtable 順序  
 `IDebugInterceptExceptionCompleteEvent2`介面實作下列的方法。  
  
|方法|描述|  
|--------|--------|  
|[GetInterceptCookie](../Topic/IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie.md)|傳回已處理的例外狀況相關聯的唯一值。|  
  
## 備註  
 這個事件會透過傳送[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)時該方法已成功地完成處理被攔截的例外狀況。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)