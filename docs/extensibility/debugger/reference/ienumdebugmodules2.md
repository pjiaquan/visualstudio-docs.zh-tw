---
title: "IEnumDebugModules2 | Microsoft Docs"
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
  - "IEnumDebugModules2"
helpviewer_keywords: 
  - "IEnumDebugModules2"
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉模組的清單。  
  
## 語法  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面來代表程式載入的模組清單。  
  
## 呼叫者的備忘稿  
 Visual Studio 的呼叫[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)以取得這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugModules2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|擷取指定的列舉型別序列中的模組。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|略過指定的數目的列舉型別序列中的模組。|  
|[重設](../Topic/IEnumDebugModules2::Reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|取得模組的數字。|  
  
## 備註  
 Visual Studio 會使用這個介面，主要是為了更新**模組**視窗。  
  
 為了偵錯在 Visual Studio 中，程式是可以跨模組界限，因此的程式碼指示以邏輯順序為一系列的單一模組需要[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。  在清單中的第一個模組通常會包含相關聯的程式的初始的進入點。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)