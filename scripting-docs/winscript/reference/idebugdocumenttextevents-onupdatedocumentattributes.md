---
title: "IDebugDocumentTextEvents::onUpdateDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onUpdateDocumentAttributes"
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onUpdateDocumentAttributes
表示文件屬性已變更。  
  
## 語法  
  
```  
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### 參數  
 `textdocattr`  
 \[in\] 新文件屬性。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會指示文件屬性已變更。  
  
## 請參閱  
 [IDebugDocumentTextEvents 介面](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [TEXT\_DOC\_ATTR 的常數](../../winscript/reference/text-doc-attr-constants.md)