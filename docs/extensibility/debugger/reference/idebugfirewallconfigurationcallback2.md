---
title: "IDebugFirewallConfigurationCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFirewallConfigurationCallback2 介面"
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

啟用偵錯引擎使用 DCOM 來問[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ，確定防火牆會封鎖遠端偵錯的 UI。  
  
## 語法  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## 實作器注意事項  
 物件實作的連接埠的工作階段的偵錯管理員 」。  
  
## 方法  
 下表顯示的方法`IDebugFirewallConfigurationCallback2`。  
  
|方法|描述|  
|--------|--------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|要求的防火牆封鎖遠端偵錯。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll