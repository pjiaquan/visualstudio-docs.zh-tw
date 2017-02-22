---
title: "IDebugQueryEngine2 | Microsoft Docs"
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
  - "IDebugQueryEngine2"
helpviewer_keywords: 
  - "IDebugQueryEngine2 介面"
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會讓偵錯管理員 \(SDM\) 擷取介面，表示偵錯引擎 \(DE\) 工作階段。  
  
## 語法  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 實作這個介面上實作常見的 DE 介面的物件 \(例如[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)， [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)，以及[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\) 若要允許存取[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) DE 本身的介面。  
  
## 呼叫者的備忘稿  
 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)在典型的 DE 介面，以取得這個介面上。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugQueryEngine2`。  
  
|方法|描述|  
|--------|--------|  
|[GetEngineInterface](../Topic/IDebugQueryEngine2::GetEngineInterface.md)|取得自訂的偵錯引擎 \(DE\) 介面。|  
  
## 備註  
 在實作的物件通常會實作這個介面[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面以支援原因訂購逐步執行函式。 也就是當偵錯工具因為跳離函式下, 一個要執行的函式可能不在堆疊上的前一個函式，但另一個執行緒中的函式完全。  如需 「 原因 」 的定義，請參閱[Visual Studio 偵錯工具的詞彙](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)