---
title: "IDebugProcessQueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties"
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面是由實作擴充介面[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)實作者。  它允許實作器取得偵錯的處理程序環境中的資訊。  
  
## 語法  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## 實作器注意事項  
 實作這個介面，以取得偵錯的處理程序的執行環境的相關資訊。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProcessQueryProperties`。  
  
|方法|描述|  
|--------|--------|  
|[QueryProperty](../Topic/IDebugProcessQueryProperties::QueryProperty.md)|屬性值的查詢。|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|屬性值的查詢。|  
  
## 備註  
 很少會實作這個介面。  
  
## 需求  
 標頭: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)