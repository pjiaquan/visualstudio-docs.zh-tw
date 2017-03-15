---
title: "IEnumDebugProcesses2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugProcesses2"
helpviewer_keywords: 
  - "IEnumDebugProcesses2"
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉在偵錯連接埠上執行的處理程序。  
  
## 語法  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者會實作這個介面來提供連接埠上執行的處理序清單。  
  
## 呼叫者的備忘稿  
 Visual Studio 的呼叫[EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)以取得這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugProcesses2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|擷取指定列舉型別序列中的處理序。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|略過指定的數目的列舉型別序列中的處理序。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../Topic/IEnumDebugProcesses2::Clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|取得列舉值中的處理程序數目。|  
  
## 備註  
 Visual Studio 會使用這個介面來填入**處理程序**視窗。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)