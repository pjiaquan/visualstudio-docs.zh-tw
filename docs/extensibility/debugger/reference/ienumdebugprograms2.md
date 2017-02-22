---
title: "IEnumDebugPrograms2 | Microsoft Docs"
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
  - "IEnumDebugPrograms2"
helpviewer_keywords: 
  - "IEnumDebugPrograms2"
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉目前的偵錯工作階段中執行的程式。  
  
## 語法  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面來提供一份由 DE 偵錯的程式。  
  
## 呼叫者的備忘稿  
 Visual Studio 的呼叫[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)以取得這個介面。  [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)不會使用 Visual Studio。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugPrograms2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugPrograms2::Next.md)|擷取指定列舉型別序列中的程式。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|略過指定的數目的列舉型別序列中的程式。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../Topic/IEnumDebugPrograms2::Clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../Topic/IEnumDebugPrograms2::GetCount.md)|取得列舉值中的程式數目。|  
  
## 備註  
 Visual Studio 會使用這個介面來：  
  
-   填入**模組**視窗 \(藉由呼叫[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) ，然後呼叫[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)上每個程式\)。  
  
-   填入**附加至處理序**清單 \(藉由呼叫`IDebugProcess2::EnumPrograms` ，然後呼叫[QueryInterface](/visual-cpp/atl/queryinterface)上每個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面，以取得[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)介面\)。  
  
-   產生一份可以偵錯的處理序中的每個程式的 DEs \(使用[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)\)。  
  
-   將編輯後繼續 \(ENC\) 更新套用至每一個程式 \(藉由呼叫 IDebugProcess2::EnumPrograms，然後呼叫[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)\)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)