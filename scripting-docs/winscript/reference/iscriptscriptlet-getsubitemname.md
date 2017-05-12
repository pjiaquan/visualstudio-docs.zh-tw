---
title: "IScriptScriptlet::GetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetSubItemName"
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptScriptlet::GetSubItemName
傳回在 scriptlet 物件的主應用程式的完整名稱的最後一個識別項。  
  
## 語法  
  
```  
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### 參數  
 `pbstr`  
 \[in\]，如果主應用程式的完整名稱 scriptlet 有多個層級， `pbstr` 傳回識別項之緩衝區的位址在第二層。  
  
 如果主應用程式的完整名稱 scriptlet 有一個層級， `pbstr` 傳回識別項之緩衝區的位址在第一個層級。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IScriptScriptlet 介面](../../winscript/reference/iscriptscriptlet-interface.md)