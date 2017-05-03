---
title: "IRemoteDebugApplicationEx 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx 介面"
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx 介面
表示執行中的應用程式。  它不需要對應到作業系統處理序。  一般來說，偵錯工具目標應用程式以進行偵錯。  同處理序偵錯處理常式通常實作應用程式物件。  
  
 除了繼承自 `IUnknown` 的方法之外，`IRemoteDebugApplicationEx` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|傳回主應用程式的處理序 ID。|  
|GetHostMachineName|傳回主應用程式執行所在電腦的名稱。|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|設定偵錯工具當地語系化的語言。|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|強制偵錯工具中逐步執行方式。|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|取消中斷命令。|  
|SetProxyBlanketAndAddRef|如需更新 COM Proxy 的安全性資訊的偵錯工具物件可以確保與遠端偵錯的相容性從 Windows 95 依作業系統而定。|  
|ReleaseFromSetProxyBlanket|從 SetProxyBlanketAndAddRef 版本 AddRef。|