---
title: "IEEVisualizerServiceProvider | Microsoft Docs"
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
  - "IEEVisualizerServiceProvider"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider 介面"
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會提供存取權的方法，可以建立視覺化檢視服務，用來處理 IDE 類型視覺化檢視的工作。  
  
## 語法  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## 實作者注意事項  
 Visual Studio 會實作這個介面可建立一個視覺化檢視服務物件，接著用來提供類別識別碼 \(`CLSID`s\) 的型別為 Visual Studio IDE 的視覺化檢視。  
  
## 呼叫端資訊  
 運算式評估工具 \(EE\) 呼叫 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) 以取得此介面。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|建立視覺化檢視服務|  
  
## 備註  
 `IEEVisualizerServiceProvider` 介面時所取得的實作 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 這個介面會建立視覺化檢視服務用來提供功能 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 介面，這卻是負責實作。 EE 也會負責實作 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 介面，可讓類型的視覺化檢視來檢視和修改屬性的值。  
  
 請參閱 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md) 如需有關這些介面互動的方式。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)