---
title: "IDebugDocumentText::GetDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetDocumentAttributes
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetDocumentAttributes"
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetDocumentAttributes
傳回文件的屬性。  
  
## 語法  
  
```  
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### 參數  
 `ptextdocattr`  
 \[in\] 文件的文字屬性。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回文件的屬性。  
  
## 請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [TEXT\_DOC\_ATTR 的常數](../../winscript/reference/text-doc-attr-constants.md)