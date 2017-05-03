---
title: "IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::OnCreateDocumentContext"
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::OnCreateDocumentContext
告知主應用程式建立新的資料內容建立並允許主應用程式會選擇性地傳回新內容的一個控制項的版本。  
  
## 語法  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### 參數  
 `ppunkOuter`  
 \[in\] 物件控制新內容。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|主機不會提供控制項物件。|  
  
## 備註  
 這個方法可讓主應用程式將新功能加入至 Helper 提供的文件內容。  在呼叫端負責建立內容的情況下，這個方法可能會傳回 **E\_NOTIMPL** 或空外部物件。  
  
## 請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)