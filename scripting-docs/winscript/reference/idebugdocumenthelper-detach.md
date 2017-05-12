---
title: "IDebugDocumentHelper::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Detach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Detach"
ms.assetid: 820b9a8c-9a88-479a-b095-daea99394f9c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Detach
從文件移除文件樹狀結構。  
  
## 語法  
  
```  
HRESULT Detach();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會從文件中移除文件樹狀結構。  
  
## 請參閱  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)