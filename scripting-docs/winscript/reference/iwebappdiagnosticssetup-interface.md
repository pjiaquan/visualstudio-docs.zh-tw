---
title: "IWebAppDiagnosticsSetup 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup 介面"
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IWebAppDiagnosticsSetup 介面
這個介面是由 PDM 實作偵錯應用程式會在偵錯之處理序的 COM 物件和啟用下列診斷。  如果 PDM 偵錯應用程式實作的物件 [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)， [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) 與其 Internet Explorer 先呼叫，然後在已建立並傳遞之後 [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449)。  WWA 應用程式 [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) 會呼叫並傳入 WWA 連接 IWebApplicationHost。  如果 [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) 呼叫具有非 null 的值， [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) 則傳回 true。  否則，會傳回錯誤，且會 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 的呼叫失敗。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` 由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 方法  
 這個介面會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|取得由指定之篩選條件隱藏的文字文件。|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|判斷指定的檔案是否屬於其中一個節點的子節點。|