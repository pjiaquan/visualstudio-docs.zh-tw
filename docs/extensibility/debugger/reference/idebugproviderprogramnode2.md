---
title: "IDebugProviderProgramNode2 | Microsoft Docs"
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
  - "IDebugProviderProgramNode2"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2"
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面之間封送處理跨處理序界限的程式相關的介面。  
  
## 語法  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 實作的同一個物件上實作這個介面[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)以支援跨處理序界限的封送處理的介面。  
  
## 呼叫者的備忘稿  
 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugProgramNode2`以取得這個介面的介面。  如果無法取得這個介面，DE 不支援介面的封送處理。  
  
## 方法 Vtable 順序  
 這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|取得指定的介面，跨處理序界限。|  
  
## 備註  
 DE 執行不同的處理序空間中，從 \[偵錯的程式時，都會實作這個介面： 例如，DE 片時 Visual Studio 的處理序空間，而不是正在偵錯程式的處理序空間中。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)