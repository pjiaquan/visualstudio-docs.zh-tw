---
title: "IDebugGenericParamField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericParamField 介面"
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugGenericParamField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示為 managed 程式碼的泛型型別參數。  
  
## 語法  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## 實作器注意事項  
 用來支援泛型。  
  
## 方法  
 除了在方法[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|傳回這個泛型參數相關聯的限制式的個數。|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|擷取這個泛型參數相關聯的條件約束。|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|擷取這個泛用參數的旗標。|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|擷取這個泛用參數的索引。|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|擷取這個泛用參數的名稱。|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|擷取這個泛用參數的型別或方法擁有者。|  
  
## 需求  
 標頭: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll