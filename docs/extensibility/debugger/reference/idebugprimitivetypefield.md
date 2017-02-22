---
title: "IDebugPrimitiveTypeField | Microsoft Docs"
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
  - "IDebugPrimitiveTypeField 介面"
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPrimitiveTypeField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示從基本型別列舉值[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。  
  
## 語法  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## 方法  
 除了在方法[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|擷取與這個欄位關聯的基本型別。|  
  
## 需求  
 標頭: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll