---
title: "IEnumDebugCustomAttributes | Microsoft Docs"
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
  - "IEnumCustomAttributes"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes 介面"
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列舉的自訂屬性。  
  
## 語法  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## 實作器注意事項  
 符號提供者會實作這個介面以支援自訂屬性 \(透過[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)介面\)。  
  
## 呼叫者的備忘稿  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)傳回這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugCustomAttributes`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|擷取指定的列舉型別序列中的自訂屬性數目。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|略過指定的數目的列舉型別序列中的自訂屬性。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../Topic/IEnumDebugCustomAttributes::Clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|取得列舉值中的自訂屬性數目。|  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)