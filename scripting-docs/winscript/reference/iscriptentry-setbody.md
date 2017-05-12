---
title: "IScriptEntry::SetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetBody"
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry::SetBody
設定 `IScriptEntry` 指令碼區塊或 `IScriptScriptlet` scriptlet 主體中的文字。  
  
## 語法  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### 參數  
 `psz`  
 \[in\] `IScriptEntry` 指令碼區塊， `psz` 是在指令碼標記括住的文字。  
  
 如需 `IScriptEntry` 函式區塊， `psz` 是函式的主體。  
  
 若要從 `IScriptEntry`衍生 `IScriptScriptlet` 的物件， `psz` 是 scriptlet 指令碼的文字。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)