---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp"
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
這個方法建立使用 `dwClsContext`ID，您可以使用 `rclsid` 的類別。  這類似於 [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) 運作的方式，不同之處在於，在 `CreateObjectWithSiteAtWebApp` 下物件在 Web 應用程式的 UI 執行緒上建立非同步。  類別指定 ID 的物件應該實作 [IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。  在建立物件之後， [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) 呼叫的 PDM 有關偵錯應用程式並 `CreateObjectWithSiteAtWebApp``hPassToObject` 參數。  您可以使用這個方法傳遞至應用程式中控制項至複製到一個 [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450)匿名管道。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup 介面](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(  
        [in] REFCLSID rclsid,   
        [in] DWORD dwClsContext,   
        [in] REFIID riid,   
        [in] DWORD_PTR hPassToObject  
        );  
  
```  
  
#### 參數  
 `rclsid`  
 建立類別的類別 ID。  
  
 `dwClsContext`  
 程式碼會執行的內容。  在大部分情況都是 CLSCTX\_INPROC\_SERVER。  
  
 `riid`  
 不適用。  
  
 `hPassToObject`  
 一次將傳給物件其值在 UI 執行緒上建立，則為，如果物件實作 [IWebAppDiagnosticsObjectInitialization 介面](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。