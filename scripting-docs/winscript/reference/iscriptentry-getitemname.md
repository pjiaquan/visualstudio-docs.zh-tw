---
title: "IScriptEntry::GetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetItemName"
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::GetItemName
傳回可識別 `IScriptEntry` 物件的項目名稱。  
  
## 語法  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### 參數  
 `pbstr`  
 \[in\] 包含項目名稱緩衝區的位址。  主應用程式會使用項目名稱識別項目。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 您可以使用 [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)，對於 `IScriptScriptlet` 物件，將項目名稱。  至於所有其他的介面，您可以使用 [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)的項目名稱。  
  
## 請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)