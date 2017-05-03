---
title: "IMachineDebugManagerCookie 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerCookie 介面"
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie 介面
類似 `IMachineDebugManager` 介面， `IMachineDebugManagerCookie` 介面支援偵錯 Cookie。  
  
 這個介面 `IDebugCookie` \(使用介面\) 在指令碼偵錯工具處理序允許執行指令碼，而不需使用偵錯工具記錄這些指令碼。  
  
 指令碼偵錯工具會在處理序的 `IDebugCookie::SetDebugCookie` 方法偵錯 Manager \(PDM\)。  然後， PDM 與所有加入要求一起傳送這個 Cookie `IMachineDebugManagerCookie` 使用介面的方法，或移除指令碼應用程式與電腦偵錯 Manager \(MDM\)。  MDM 接著會通知變更的每個偵錯工具，但具有該 Cookie 的值。  
  
 除了繼承自 `IUnknown` 的方法之外，`IMachineDebugManagerCookie` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|將應用程式加入至執行中的應用程式清單。|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|傳回正在執行的應用程式目前清單的列舉值。|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|執行應用程式的清單中移除應用程式。|  
  
## 請參閱  
 [IMachineDebugManager 介面](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie 介面](../../winscript/reference/idebugcookie-interface.md)