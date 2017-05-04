---
title: "IDebugAsyncOperation::GetSyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetSyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetSyncDebugOperation"
ms.assetid: ff89a3bc-57d7-4cb9-9818-8d73ed71af73
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetSyncDebugOperation
傳回同步偵錯作業與這個物件相關聯的。  
  
## 語法  
  
```  
HRESULT GetSyncDebugOperation(  
   IDebugSyncOperation**  ppsdo  
);  
```  
  
#### 參數  
 `ppsdo`  
 \[in\] 同步偵錯作業與這個物件相關聯的。  
  
## 傳回值  
 Il metodo restituisce un tipo `HRESULT`.  可能的值包括，，但不限於\)，這些在下表中。  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## 備註  
 這個方法會傳回同步處理的偵錯作業與這個物件相關聯的。  
  
## 請參閱  
 [IDebugAsyncOperation 介面](../../winscript/reference/idebugasyncoperation-interface.md)