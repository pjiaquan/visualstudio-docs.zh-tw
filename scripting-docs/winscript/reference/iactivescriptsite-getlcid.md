---
title: "IActiveScriptSite::GetLCID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetLCID"
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetLCID
擷取地區設定識別項與主應用程式的使用者介面。  指令碼引擎使用識別項保證引擎和其他使用者介面項目產生的錯誤字串會出現在適當的語言。  
  
## 語法  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### 參數  
 `plcid`  
 \[out\] 接收使用者介面項目的地區設定識別項變數位址由指令碼引擎已顯示。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|這個方法尚未實作。  使用系統定義的地區設定。|  
|`E_POINTER`|無效的指標被指定。|  
  
## 備註  
 如果這個方法會傳回 `E_NOTIMPL`，應該使用系統定義的地區設定識別項。  
  
## 請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)