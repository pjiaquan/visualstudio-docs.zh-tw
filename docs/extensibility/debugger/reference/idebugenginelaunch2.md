---
title: "IDebugEngineLaunch2 | Microsoft Docs"
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
  - "IDebugEngineLaunch2"
helpviewer_keywords: 
  - "IDebugEngineLaunch2 介面"
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用來啟動和終止程式偵錯引擎 \(DE\)。  
  
## 語法  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## 實作器注意事項  
 如果已經啟動自訂的通訊埠無法完全處理的處理序的特殊需求，自訂 DE 會實作這個介面。  這通常是當 DE 屬於直譯器，並且處理程序進行偵錯指令碼: 直譯器必須先啟動，然後載入並啟動指令碼。  連接埠可以啟動直譯器，但指令碼可能會需要特別處理 \(也就是其中 DE 都有一個角色\)。  獨特的需求，來啟動自訂的通訊埠無法處理的程式時，才會實作這個介面。  
  
## 呼叫者的備忘稿  
 這個介面由呼叫 「 工作階段偵錯管理員 」 \(SDM\) 是否 SDM 可以取得這個介面從[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面 \(使用 QueryInterface\)。  如果可以取得這個介面，SDM 會知道 DE 有特殊需求，並且呼叫這個介面來啟動程式，而不要讓它啟動的連接埠。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugEngineLaunch2`。  
  
|方法|描述|  
|--------|--------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|DE 啟動處理序。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|便會繼續處理執行。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|決定是否可以終止處理程序。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|結束處理程序。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)