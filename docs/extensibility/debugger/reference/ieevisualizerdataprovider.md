---
title: "IEEVisualizerDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider 介面"
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會提供變更物件的值類型的視覺化檢視的能力。  
  
## 語法  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## 實作者注意事項  
 運算式評估工具會實作這個介面以支援透過型別視覺化檢視的屬性物件上修改資料。  
  
## 呼叫端資訊  
 這個介面會用於建立 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 物件，用來呼叫 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)。 如需詳細資訊，請參閱 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[CanSetObjectForVisualizer](../Topic/IEEVisualizerDataProvider::CanSetObjectForVisualizer.md)|判斷是否可以更新物件 （和之後，其值），代表這個視覺化檢視。|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|這個視覺化檢視的強制重新評估的物件。|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|取得這個視覺化檢視 （不進行評估完成） 的現有物件。|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|這個視覺化檢視，藉此變更視覺化檢視所顯示的值會更新物件。|  
  
## 備註  
 視覺化檢視服務 \(所表示的 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 介面，並傳回 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\) 保留參考物件實作 `IEEVisualizerDataProvider` 介面。 如此一來， `IEEVisualizerDataProvider` 不應該實作的相同物件上實作介面 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 如果該物件會維護的參考 `IEEVisualizerService` 物件︰ 產生循環參考，以及當物件終結時，就會發生死結。 建議的方法是實作 `IEEVisualizerDataProvider` 上的個別物件的 `IDebugProperty2` 物件而不需呼叫委派 `IUnknown::AddRef` 在其上。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)