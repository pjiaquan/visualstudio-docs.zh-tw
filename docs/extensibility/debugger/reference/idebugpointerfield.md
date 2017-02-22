---
title: "IDebugPointerField | Microsoft Docs"
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
  - "IDebugPointerField"
helpviewer_keywords: 
  - "IDebugPointerField 介面"
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示指標型別。  
  
## 語法  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## 實作器注意事項  
 符號提供者會實作這個介面來代表變數的指標。  
  
## 呼叫者的備忘稿  
 使用[QueryInterface](/visual-cpp/atl/queryinterface)以取得這個介面，從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面如果[GetKind](../Topic/IDebugField::GetKind.md)會傳回`FIELD_TYPE_POINTER`。  
  
## 方法 Vtable 順序  
 除了在方法`IDebugField`和`IDebugContainerField`介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述指標的目標。|  
  
## 備註  
 在 C\/c \+ \+，變數的指標可以是容器，如果它使用陣列標記法。  例如，假設`char *pString`， `pString`有指向指標的一種`char`。  `pString[3]`具有型別的一種容器，它是指向`char`會參考該容器的第四個項目。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)