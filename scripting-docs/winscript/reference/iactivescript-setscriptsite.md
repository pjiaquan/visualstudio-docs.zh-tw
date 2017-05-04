---
title: "IActiveScript::SetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptSite"
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::SetScriptSite
告知主應用程式所提供的指令碼引擎 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 介面網站。  在使用之前，呼叫這個方法 [IActiveScript](../../winscript/reference/iactivescript.md) 任何其他介面方法。  
  
## 語法  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### 參數  
 `pScriptSite`  
 \[in\] 要產生關聯的主應用程式提供的指令碼網站的位址與指令碼引擎的執行個體。  必須唯一地將該網站加入至指令碼引擎的執行個體;它不能與其他指令碼引擎共用。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_FAIL`|未指定的錯誤，指令碼引擎無法完成初始化這個網站。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，站台已設定\)。|  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)