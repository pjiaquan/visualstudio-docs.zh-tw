---
title: "IScriptEntry::SetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetItemName"
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetItemName
設定辨識 `IScriptEntry` 物件的項目名稱。  
  
## 語法  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### 參數  
 `psz`  
 \[in\] 包含項目名稱緩衝區的位址。  主應用程式會使用項目名稱識別項目。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法不會成功。|  
  
## 備註  
 對於 `IScriptEntry` 物件，這個方法會傳回 `S_OK`。  
  
 對於從 `IScriptEntry`衍生的 `IScriptScriptlet` 物件，這個方法會傳回 `E_FAIL`。  對於物件， `IScriptScriptlet` 項目名稱由 [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) 設定，無法變更。  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)