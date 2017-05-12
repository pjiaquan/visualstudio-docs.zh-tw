---
title: "IActiveScriptSiteWindow::EnableModeless | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_EnableModeless"
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow::EnableModeless
讓主應用程式啟用或停用其主視窗以及所有非強制回應對話方塊。  
  
## 語法  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### 參數  
 `fEnable`  
 \[in\] 旗標，請，如果 `TRUE`，啟用主視窗和非強制回應對話方塊，或者，如果 `FALSE`，停用它們。  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_FAIL`，如果發生錯誤則為。  
  
## 備註  
 這個方法 `IOleInPlaceFrame::EnableModeless` 與方法相同。  
  
 對這個方法的呼叫可以是巢狀結構。  
  
## 請參閱  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)