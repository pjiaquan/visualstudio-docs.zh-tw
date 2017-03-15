---
title: "IEEVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerService 介面"
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IEEVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會實作提供功能的主要方法 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 和 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 介面。  
  
## 語法  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## 實作者注意事項  
 Visual Studio 會實作這個介面，讓運算式評估工具 \(EE\) 以支援類型的視覺化檢視。  
  
## 呼叫端資訊  
 EE 呼叫 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) 這個介面做為其支援的一部分取得類型的視覺化檢視。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|擷取這項服務知道哪些自訂的檢視器的數目。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|擷取自訂檢視器的清單。|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|傳回屬性的 proxy 物件。|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|擷取值的字串，以顯示指定的屬性或欄位的數目。|  
  
## 備註  
 IDE 會使用 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 介面，以判斷是否有任何自訂的檢視器，或輸入屬性的視覺化檢視。 藉由建立視覺化檢視服務 \(與 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\)，卻可以提供的功能 `IDebugProperty3` 和 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) （可支援檢視和變更屬性的值） 介面，並藉此支援類型的視覺化檢視。  
  
 如果 EE 具有自訂檢視器本身實作中，可以附加 EE `CLSID`所傳回的清單結尾的自訂檢視器之 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。 這可讓 EE 支援類型的視覺化檢視和它自己的自訂檢視器。 只是無法確定 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) 反映加入的任何自訂的檢視器。  
  
 請參閱 [類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 視覺化檢視和檢視器之間的差異的討論。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)