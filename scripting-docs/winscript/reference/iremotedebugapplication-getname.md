---
title: "IRemoteDebugApplication::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetName"
ms.assetid: 3a8e8a4b-d7d4-40e5-97a1-f6d18db2e9c4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetName
傳回此應用程式的名稱。  
  
## 語法  
  
```  
HRESULT GetName(  
   BSTR*  pbstrName  
);  
```  
  
#### 參數  
 `pbstrName`  
 \[in\] 此應用程式的名稱。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回這個應用程式的名稱。  
  
## 請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)