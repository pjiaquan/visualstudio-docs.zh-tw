---
title: "IDebugFunctionPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionPosition2"
helpviewer_keywords: 
  - "IDebugFunctionPosition2 介面"
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示來源文件中的函式的抽象座標。  
  
## 語法  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面來表示來源文件中的函式的位置。  
  
## 呼叫者的備忘稿  
 這個介面會提供做為一部分的[BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)等位 \(明確地說， [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)結構\) 屬於又[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構，用來建立暫止中斷點。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugFunctionPosition2`。  
  
|方法|描述|  
|--------|--------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|取得這個位置是相對於函式名稱。|  
|[GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)|取得從函式開頭的位移。|  
  
## 備註  
 這個介面所表示的位置是以文字為主，特別是， [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)