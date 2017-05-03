---
title: "IDebugDocumentInfo::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetName"
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetName
傳回指定的檔案名稱。  
  
## 語法  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### 參數  
 `dnt`  
 \[in\] 文件名稱的型別所傳回的。  
  
 `pbstrName`  
 \[in\] 包含名稱的字串。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|指定的檔案名稱不明。|  
  
## 備註  
 這個方法會傳回指定的檔案名稱。  
  
## 請參閱  
 [IDebugDocumentInfo 介面](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE 列舉](../../winscript/reference/documentnametype-enumeration.md)