---
title: "IDebugModule2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2"
helpviewer_keywords: 
  - "IDebugModule2 介面"
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugModule2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示模組 — 也就是程式的可執行單位，例如 DLL。  
  
## 語法  
  
```  
IDebugModule2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面表示模組，並提供該模組的相關資訊的存取權。  
  
## 呼叫者的備忘稿  
 呼叫[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)會傳回這個介面。  DE 傳送[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)介面，以使用 「 工作階段偵錯管理員 」 \(SDM\) [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。  
  
 此介面也可能會傳回在[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構 \(它會傳回呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)\)。  
  
 [下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)也會傳回這個介面 \([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)會傳回[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)介面\)。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugModule2`。  
  
|方法|描述|  
|--------|--------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|取得[MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) ，告訴您，本單元。|  
|[ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|已過時。  請勿使用。  重新載入這個模組的符號。|  
  
## 備註  
 模組的資訊會顯示在**模組**在 ide 的視窗。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)