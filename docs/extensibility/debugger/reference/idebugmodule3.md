---
title: "IDebugModule3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3"
helpviewer_keywords: 
  - "IDebugModule3 介面"
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModule3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示模組可支援的符號和 JustMyCode 狀態的替代位置。  
  
## 語法  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面支援替代位置的符號，並使用 JustMyCode 狀態 \(請參閱[Visual Studio 偵錯工具的詞彙](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) "JustMyCode"的定義\)。  
  
## 呼叫者的備忘稿  
 呼叫[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)會傳回這個介面。  DE 傳送[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)介面，以使用 「 工作階段偵錯管理員 」 \(SDM\) [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。  此外，呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)介面會傳回這個介面。  
  
## 方法 Vtable 順序  
 除了在方法[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|傳回一份符號與搜尋每個路徑的結果中搜尋的路徑。|  
|[LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)|載入並初始化目前模組的符號。|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|傳回旗標，指定此模組是否代表使用者程式碼。|  
|[SetJustMyCodeState](../Topic/IDebugModule3::SetJustMyCodeState.md)|指定是否將模組應考慮使用者程式碼與否。|  
  
## 備註  
 Visual Studio 是典型的取用者，此介面。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)