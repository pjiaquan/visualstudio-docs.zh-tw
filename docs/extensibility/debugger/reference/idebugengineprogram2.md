---
title: "IDebugEngineProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2"
helpviewer_keywords: 
  - "IDebugEngineProgram2 介面"
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會提供多執行緒偵錯支援。  
  
## 語法  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎會實作這個介面以支援多個執行緒同時偵錯。  在實作的同一個物件上實作這個介面[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。  
  
## 呼叫者的備忘稿  
 使用[QueryInterface](/visual-cpp/atl/queryinterface)以取得這個介面，從`IDebugProgram2`介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugEngineProgram2`。  
  
|方法|描述|  
|--------|--------|  
|[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|停止執行此程式中的所有執行緒。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|執行 \(或執行監看的停駐點\) 會監看發生於指定的執行緒。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|允許 \(或不允許\) 發生於指定的執行緒中，即使程式停止運算式評估。|  
  
## 備註  
 Visual Studio 會呼叫此介面，以回應[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件，並設定 「 執行緒步驟監看式 」 和 「 監看式的運算式評估的執行緒 」 狀態的程式。  [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)此程式會停止的狀態 ； 只要會呼叫 這個方法會讓程式有機會終止所有的執行緒。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)