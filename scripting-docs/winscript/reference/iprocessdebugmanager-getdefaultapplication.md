---
title: "IProcessDebugManager::GetDefaultApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.GetDefaultApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::GetDefaultApplication"
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::GetDefaultApplication
傳回目前處理序的預設應用程式物件。  
  
## 語法  
  
```  
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### 參數  
 `ppda`  
 \[out\] 此應用程式的應用程式進行偵錯的物件。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會建立新的應用程式進行偵錯的物件並將它加入至執行中的應用程式清單，如果需要。  
  
 語言引擎應該使用 `GetDefaultApplication` 方法所指定的應用程式中，它們就不會提供應用程式的主應用程式執行。  
  
## 請參閱  
 [IProcessDebugManager 介面](../../winscript/reference/iprocessdebugmanager-interface.md)