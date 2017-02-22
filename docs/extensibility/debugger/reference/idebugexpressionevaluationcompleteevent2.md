---
title: "IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs"
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
  - "IDebugExpressionEvaluationCompleteEvent2"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2"
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會傳送偵錯引擎 \(DE\) 給工作階段的偵錯專案經理 \(SDM\) 完成非同步運算式評估時。  
  
## 語法  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面來報告完成的運算式評估啟動呼叫[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作這個介面以相同的物件。  SDM 會使用[QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## 呼叫者的備忘稿  
 DE 建立並傳送報告的運算式評估完成此事件物件。  使用傳送事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加至正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugExpressionEvaluationCompleteEvent2`。  
  
|方法|描述|  
|--------|--------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|取得原始的運算式。|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|取得運算式的評估的結果。|  
  
## 備註  
 評估是否成功，或不，DE 必須傳送這個事件。  
  
 如果評估結果不成功， `DEBUG_PROPINFO_VALUE`和`DEBUG_PROPINFO_ATTRIB`旗標將不會設定[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)所傳回的結構[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) \( [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) DE 所建立的物件並傳回`IDebugExpressionEvaluationCompleteEvent2`如果評估失敗的事件\)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)