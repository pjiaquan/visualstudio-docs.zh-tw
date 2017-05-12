---
title: "IDebugDocumentHelper::SetDocumentAttr | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDocumentAttr
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDocumentAttr"
ms.assetid: bd7ffdbd-de51-477d-bd3f-760db020fe70
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDocumentAttr
設定這個文件的屬性。  
  
## 語法  
  
```  
HRESULT SetDocumentAttr(  
   TEXT_DOC_ATTR  pszAttributes  
);  
```  
  
#### 參數  
 `pszAttributes`  
 \[in\] 要套用的屬性於文件中。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會設定文件的屬性。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT\_DOC\_ATTR 的常數](../../winscript/reference/text-doc-attr-constants.md)