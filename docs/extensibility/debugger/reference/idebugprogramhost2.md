---
title: "IDebugProgramHost2 | Microsoft Docs"
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
  - "IDebugProgramHost2"
helpviewer_keywords: 
  - "IDebugProgramHost2 介面"
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會提供程式的主機 \(處理程序\) 資訊。  
  
## 語法  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎實作這個介面上相同的物件，做為[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面，以提供裝載處理序的相關資訊。  這是選擇性的介面。  
  
## 呼叫者的備忘稿  
 呼叫[QueryInterface](/visual-cpp/atl/queryinterface)的`IDebugProgram2`以取得這個介面的介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProgramHost2`。  
  
|方法|描述|  
|--------|--------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|取得標題、 好記的名稱或檔名的裝載處理序，此程式。|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|取得裝載處理序，這個程式的處理序識別項。|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|取得的電腦執行此程式使用裝載處理序的名稱。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)