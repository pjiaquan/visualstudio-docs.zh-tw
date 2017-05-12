---
title: "IWebAppDiagnosticsObjectInitialization 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization 介面"
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsObjectInitialization 介面
這個介面在實作 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)的類別上實作。  [IWebAppDiagnosticsSetup 介面](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 物件會實作實作 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)。  在許多情況下這個物件是 PDM。  
  
 在建立物件之後， [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) 呼叫的 PDM 有關偵錯應用程式並 `CreateObjectWithSiteAtWebApp``hPassToObject` 參數。  
  
> [!IMPORTANT]
>  在`IWebAppDiagnosticsObjectInitialization` activdbg100.h. 中找到。  
  
## 方法  
 這個介面會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|初始化物件。|