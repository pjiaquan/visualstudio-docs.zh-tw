---
title: "IActiveScript::GetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptSite"
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::GetScriptSite
擷取站台物件與視窗指令碼引擎。  
  
## 語法  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### 參數  
 `iid`  
 \[in\] 要求之介面的識別項。  
  
 `ppvSiteObject`  
 \[out\] 接收介面指標給裝載的網站物件之位置的位址。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_NOINTERFACE`|指定的介面不支援。|  
|`E_POINTER`|無效的指標被指定。|  
|`S_FALSE`|站台尚未設定; `ppvSiteObject` 參數設定為 `NULL`。|  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)