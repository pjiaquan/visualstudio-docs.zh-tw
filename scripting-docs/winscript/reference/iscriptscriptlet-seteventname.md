---
title: "IScriptScriptlet::SetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetEventName"
ms.assetid: 8787d58b-7deb-415b-b0e9-d2f0eb72dcf7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IScriptScriptlet::SetEventName
設定與 scriptlet 事件的名稱。  
  
## 語法  
  
```  
HRESULT SetEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### 參數  
 `psz`  
 \[in\] 包含事件名稱與 `IScriptScriptlet` 物件的緩衝區。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IScriptScriptlet 介面](../../winscript/reference/iscriptscriptlet-interface.md)