---
title: "IActiveScriptSite::GetDocVersionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetDocVersionString"
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetDocVersionString
擷取可唯一識別目前的檔案版本的主應用程式定義的字串。  如果相關檔案已變更視窗中的範圍以外的指令碼 \(如在編輯與記事本\) 的 HTML 網頁的情況下，指令碼引擎可以與其持續性 \(Persistent\) 狀態儲存在一起，這會強制重新編譯，下次載入指令碼。  
  
## 語法  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### 參數  
 `pstrVersionString`  
 \[in\] 主應用程式定義的文件版本字串的位址。  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_NOTIMPL` ，則這個方法不受支援。  
  
## 備註  
 如果 `E_NOTIMPL` 傳回，指令碼引擎應該假設，指令碼一致的文件。  
  
## 請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)