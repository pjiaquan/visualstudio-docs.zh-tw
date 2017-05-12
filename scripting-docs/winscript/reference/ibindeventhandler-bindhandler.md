---
title: "IBindEventHandler::BindHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IBindEventHandler.BindHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IBindEventHandler::BindHandler"
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IBindEventHandler::BindHandler
要繫結至物件的事件。  
  
## 語法  
  
```  
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### 參數  
 `pstrEvent`  
 \[in\] 指定事件處理常式。  
  
 `pdisp`  
 \[in\] 指定物件來處理事件。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法所繫結的事件物件。  
  
## 請參閱  
 [IBindEventHandler 介面](../../winscript/reference/ibindeventhandler-interface.md)