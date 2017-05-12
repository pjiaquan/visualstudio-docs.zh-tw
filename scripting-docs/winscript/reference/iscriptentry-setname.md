---
title: "IScriptEntry::SetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetName"
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::SetName
針對代表單一物件的項目 \(例如函式\)，設定物件的名稱。  
  
## 語法  
  
```  
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### 參數  
 `psz`  
 \[in\] `IScriptEntry` 物件的新名稱。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)