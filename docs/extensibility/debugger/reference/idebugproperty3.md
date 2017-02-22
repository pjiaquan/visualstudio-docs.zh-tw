---
title: "IDebugProperty3 | Microsoft Docs"
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
  - "IDebugProperty3"
helpviewer_keywords: 
  - "IDebugProperty3 介面"
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會提供對支援：  
  
-   擷取與屬性相關聯的任意長度的字串。  
  
-   與屬性關聯的唯一 ID。  
  
-   正在擷取屬性的自訂檢視器的清單。  
  
-   設定屬性的值，能夠報告產生的錯誤  
  
## 語法  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 實作的同一個物件上實作這個介面[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)提供支援的長字串、 屬性識別碼，以及自訂的檢視器。  
  
## 呼叫者的備忘稿  
 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugProperty2`以取得這個介面的介面。  
  
## 方法 Vtable 順序  
 除了繼承自 `IDebugProperty2` 的方法之外，`IDebugProperty3` 介面還會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|傳回與屬性相關聯的字串長度。|  
|[GetStringChars](../Topic/IDebugProperty3::GetStringChars.md)|傳回使用者提供的緩衝區中的字串。|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|建立這個屬性的唯一 ID。|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|終結這個屬性的專一識別碼。|  
|[GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)|傳回這個屬性可以檢視使用的自訂檢視器的數目。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|傳回這個屬性可以檢視使用的自訂檢視器的清單。|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|設定這個屬性，傳回錯誤訊息，如果任何項目發生錯誤的值。|  
  
## 備註  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)在工作階段偵錯管理員 」 \(SDM\) 設定屬性的值是較佳的方式。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)