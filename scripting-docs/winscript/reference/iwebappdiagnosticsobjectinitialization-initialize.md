---
title: "IWebAppDiagnosticsObjectInitialization::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization::Initialize"
ms.assetid: 7ccfac28-9f65-4e1c-a0fb-a8a6c7f75b63
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IWebAppDiagnosticsObjectInitialization::Initialize
初始化一個物件建立 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)。  
  
> [!IMPORTANT]
>  在[IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) activdbg100.h. 中找到。  
  
## 語法  
  
```cpp  
HRESULT Initialize(  
        [in, annotation("__in")] HANDLE_PTR hPassedHandle,  
        [in, annotation("__in")] IUnknown* pDebugApplication  
        );  
```  
  
#### 參數  
 `hPassedHandle`  
 傳遞給 `hPassToObject` 參數的 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 方法的控制代碼。  
  
 `pDebugApplication`  
 建立物件的 PDM 應用程式。