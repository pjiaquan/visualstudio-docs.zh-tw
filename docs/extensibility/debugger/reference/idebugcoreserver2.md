---
title: "IDebugCoreServer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2"
helpviewer_keywords: 
  - "IDebugCoreServer2 介面"
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此介面用來代表，從網路上的電腦上的伺服器取得資訊。  
  
## 語法  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## 實作器注意事項  
 Visual Studio 會實作這個介面表示伺服器。  每個 Visual Studio 的執行個體建立這個介面的執行個體。  
  
## 呼叫者的備忘稿  
 自訂的連接埠提供者會收到這個介面的呼叫[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。  
  
 偵錯引擎可以取得這個介面，間接透過呼叫[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) \(會傳回[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)，介面是衍生自`IDebugCoreServer2`\)。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugCoreServer2`。  
  
|方法|描述|  
|--------|--------|  
|[GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)|取得的名稱與機器的屬性。|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|取得電腦名稱。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|取得在電腦上的一個存在的連接埠供應商。|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|取得已存在於電腦的連接埠。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|在電腦上建立的所有連接埠的列舉值。|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|在電腦上建立所有連接埠供應商的列舉的值。|  
|[GetMachineUtilities\_V7](../Topic/IDebugCoreServer2::GetMachineUtilities_V7.md)|取得電腦的機器公用程式。|  
  
## 備註  
 Visual Studio 也會使用這個介面來瀏覽網路上的電腦上執行的處理程序。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)