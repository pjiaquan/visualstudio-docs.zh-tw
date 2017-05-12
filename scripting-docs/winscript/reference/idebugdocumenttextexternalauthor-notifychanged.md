---
title: "IDebugDocumentTextExternalAuthor::NotifyChanged | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::NotifyChanged"
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::NotifyChanged
告知主應用程式文件來源變更。  
  
## 語法  
  
```  
HRESULT NotifyChanged();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法是由外部編輯器呼叫，以修改檔案架構偵錯工具資料並儲存告知主應用程式文件來源之後已經變更。  主應用程式接著重新整理文件從原始程式檔。  
  
## 請參閱  
 [IDebugDocumentTextExternalAuthor 介面](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)