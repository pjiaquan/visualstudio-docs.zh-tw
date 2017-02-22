---
title: "IDebugClassField | Microsoft Docs"
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
  - "IDebugClassField"
helpviewer_keywords: 
  - "IDebugClassField 介面"
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會表示類別，做為型別。  
  
## 語法  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## 實作器注意事項  
 符號提供者實作的同一個物件上實作這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面。  這個介面會是特製化，表示類別型別。  
  
## 呼叫者的備忘稿  
 介面的數目有方法，可能會傳回這個介面包括[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)， [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)，以及[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)。  此外，您可以使用[QueryInterface](/visual-cpp/atl/queryinterface)以取得這個介面，從[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面如果[GetKind](../Topic/IDebugField::GetKind.md)方法會傳回旗標`FIELD_TYPE_CLASS`。  
  
## 方法 Vtable 順序  
 除了在方法[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)和[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面，這個介面會實作下列：  
  
|方法|描述|  
|--------|--------|  
|[EnumBaseClasses](../Topic/IDebugClassField::EnumBaseClasses.md)|建立這個類別的基底類別的列舉值。|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|決定是否特定的介面會定義在類別中。|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|建立這個類別的巢狀類別列舉值。|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|取得圍住此類別的類別。|  
|[EnumInterfacesImplemented](../Topic/IDebugClassField::EnumInterfacesImplemented.md)|建立這個類別所實作之介面的列舉值。|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|建立這個類別的建構函式的列舉值。|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|取得預設索引子的名稱。|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|建立巢狀列舉值，這個類別的列舉值。|  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)