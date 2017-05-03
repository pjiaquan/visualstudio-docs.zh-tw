---
title: "IDebugApplication::StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StartDebugSession
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StartDebugSession"
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StartDebugSession
如果還沒有附加，啟動預設偵錯工具整合式開發環境 \(IDE\) \(IDE\) 並附加偵錯工作階段之間的這個應用程式。  
  
## 語法  
  
```  
HRESULT StartDebugSession();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法來實作 Just\-In\-Time 偵錯。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)