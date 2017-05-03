---
title: "IActiveScriptSiteWindow::GetWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_GetWindow"
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteWindow::GetWindow
擷取控制代碼可以做為快顯視窗主控的指令碼引擎必須顯示的視窗。  
  
## 語法  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### 參數  
 `phwnd`  
 \[out\] 接收視窗控制代碼變數的位址。  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_FAIL` ，如果發生錯誤則為。  
  
## 備註  
 這個方法類似於 `IOleWindow::GetWindow` 方法。  
  
## 請參閱  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)