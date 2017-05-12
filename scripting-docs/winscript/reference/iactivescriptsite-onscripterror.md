---
title: "IActiveScriptSite::OnScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptError"
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptError
告知主應用程式執行時發生錯誤，當引擎執行指令碼時。  
  
## 語法  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### 參數  
 `pase`  
 \[in\] 錯誤物件的 [IActiveScriptError](../../winscript/reference/iactivescripterror.md) 介面的位址。  主應用程式可以使用這個介面會取得有關執行錯誤的相關資訊。  
  
## 傳回值  
 傳回 `S_OK` ，如果錯誤正確處理以來，或 OLE 則為定義的錯誤碼。  
  
## 請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)