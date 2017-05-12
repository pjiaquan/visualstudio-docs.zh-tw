---
title: "IActiveScriptSiteWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteWindow 介面"
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow
這個介面以支援物件的使用者介面和 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 的主機所實作。  不支援使用者介面 \(UI\)，例如伺服器的主機，則不會實作介面 `IActiveScriptSiteWindow` 。  指令碼引擎會藉由呼叫 `QueryInterface` 存取這個介面會從 `IActiveScriptSite`。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|擷取可做為快顯視窗主控的指令碼引擎必須顯示的視窗控制代碼。|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|讓主應用程式啟用或停用其主視窗以及所有非強制回應對話方塊。|  
  
## 請參閱  
 [動態指令碼的介面](../../winscript/reference/active-script-interfaces.md)