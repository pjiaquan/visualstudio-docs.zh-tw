---
title: "IEnumDebugPropertyInfo2 | Microsoft Docs"
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
  - "IEnumDebugPropertyInfo2"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2"
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。  
  
## 語法  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面來代表特定內容的資訊。  
  
## 呼叫者的備忘稿  
 呼叫[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)以取得這個介面表示特定屬性的子系。  呼叫[EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)以取得這個介面代表特定的堆疊框架的內容。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugPropertyInfo2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|擷取指定的數目的[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)列舉型別序列中的結構。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|略過指定的數目的[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)列舉型別序列中的結構。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../Topic/IEnumDebugPropertyInfo2::GetCount.md)|取得的[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)列舉值中的結構。|  
  
## 備註  
 一般情況下，屬性是名稱、 值、 地址，以及型別，可以包含的資訊，以及任何其他的資訊適用於相關聯的屬性的物件或堆疊框架的階層架構。  如需詳細資訊，請參閱 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)