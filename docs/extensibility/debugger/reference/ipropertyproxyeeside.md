---
title: "IPropertyProxyEESide | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide"
helpviewer_keywords: 
  - "IPropertyProxyEESide 介面"
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會提供方法，以檢視相關聯的物件上的資料。  這個介面是型別視覺化檢視支援的一部分。  
  
## 語法  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## 實作器注意事項  
 運算式評估工具會實作這個介面以支援型別視覺化檢視。  
  
## 呼叫者的備忘稿  
 呼叫[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)以取得這個介面。  呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面，以取得[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面。  
  
## 方法 Vtable 順序  
 此介面將會執行下列方法：  
  
|方法|描述|  
|--------|--------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|如此可存取物件的資料，會初始化資料來源提供者。|  
|[GetManagedViewerCreationData](../Topic/IPropertyProxyEESide::GetManagedViewerCreationData.md)|擷取物件的組件有關的資訊。|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|取得物件的初始資料。|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|建立一份現有的資料儲存區。|  
|[InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md)|建立參考到現有的資料存放區。|  
|[ResolveAssemblyRef](../Topic/IPropertyProxyEESide::ResolveAssemblyRef.md)|擷取包含這個物件的組件的內容中的特定組件的相關資訊。|  
  
## 備註  
 型別視覺化檢視會使用這個介面來存取這個介面屬於該物件相關聯的值。  資料便會透過[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)介面，可提供資料的唯讀檢視。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)