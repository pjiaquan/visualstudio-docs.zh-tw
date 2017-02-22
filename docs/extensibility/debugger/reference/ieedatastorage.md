---
title: "IEEDataStorage | Microsoft Docs"
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
  - "IEEDataStorage"
helpviewer_keywords: 
  - "IEEDataStorage 介面"
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEDataStorage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示位元組的陣列。  
  
## 語法  
  
```  
IEEDataStorage : IUnknown  
```  
  
## 實作器注意事項  
 運算式評估工具 \(EE\) 會實作這個介面來表示的位元組陣列 \(用來擷取，並變更資料型別視覺化檢視[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面\)。  得知 ee 給予通常會實作這個介面以支援外部型別視覺化檢視。  
  
## 呼叫者的備忘稿  
 上的方法`IPropertyProxyEESide`所有的介面會傳回這個介面。  呼叫[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)以取得[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面。  呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面，以取得[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面。  
  
## 方法 Vtable 順序  
 `IEEDataStorage`介面實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetData](../Topic/IEEDataStorage::GetData.md)|擷取指定的資料來提供的緩衝區的位元組數。|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|擷取可用的資料位元組數目。|  
  
## 備註  
 這個介面的型別視覺化檢視用於存取特定的物件所持有的資料。  資料會被視為一系列位元組，可讓型別視覺化檢視，以中若有必要提供給使用者的方式操作它。  
  
 自訂的檢視器也可以使用這個介面，如有需要，但是更常見的是，自訂的檢視器會使用自訂的介面， [GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md)或[GetStringChars](../Topic/IDebugProperty3::GetStringChars.md) \(適用於字串為導向的資料\)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)