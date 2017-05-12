---
title: "IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.GetPathName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::GetPathName"
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::GetPathName
傳回文件的完整路徑和檔名。  
  
## 語法  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### 參數  
 `pbstrLongName`  
 \[in\] 字串包含完整路徑和檔名。  
  
 `pfIsOriginalFile`  
 \[out\] 布林值的路徑和檔案名稱是否參考原始文件中。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|無法建立或判斷原始程式檔。|  
  
## 備註  
 這個方法會傳回文件的完整路徑和檔名。  
  
 如果 `pfIsOriginalFile` 為 false，路徑和檔案名稱。 `pbstrLongName` 參考一個新建立的暫存檔案。  
  
## 請參閱  
 [IDebugDocumentTextExternalAuthor 介面](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)