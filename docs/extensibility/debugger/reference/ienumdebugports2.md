---
title: "IEnumDebugPorts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2"
helpviewer_keywords: 
  - "IEnumDebugPorts2"
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉電腦或連接埠的供應商的連接埠。  
  
## 語法  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者會實作這個介面代表 \[供應商所建立的連接埠清單。  Visual Studio 會實作這個介面，在它自己的連接埠提供者。  
  
## 呼叫者的備忘稿  
 呼叫[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)以取得這個介面代表連接埠提供者所建立的連接埠清單。  呼叫[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)以取得這個介面表示一份已儲存的連接埠至磁碟。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugPorts2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|擷取指定的列舉型別序列中的連接埠數目。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|略過指定的數目的列舉型別序列中的連接埠。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../Topic/IEnumDebugPorts2::GetCount.md)|取得列舉值中的連接埠數目。|  
  
## 備註  
 Visual Studio 會使用這個介面，來協助填入附加至處理序所使用的連接埠清單。  
  
 偵錯引擎通常不使用這個介面。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)