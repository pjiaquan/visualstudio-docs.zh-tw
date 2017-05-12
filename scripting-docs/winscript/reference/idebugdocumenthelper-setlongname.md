---
title: "IDebugDocumentHelper::SetLongName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetLongName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetLongName"
ms.assetid: b6199e5d-9b54-43a2-9775-214b8d022607
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetLongName
將完整名稱為 CAXXXX:FriendlyTypeName 文件。  
  
## 語法  
  
```  
HRESULT SetLongName(  
   LPCOLESTR  pszLongName  
);  
```  
  
#### 參數  
 `pszLongName`  
 \[in\] null 結尾包含文件的完整名稱的字串。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會設定新的完整名稱為 CAXXXX:FriendlyTypeName 文件。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)