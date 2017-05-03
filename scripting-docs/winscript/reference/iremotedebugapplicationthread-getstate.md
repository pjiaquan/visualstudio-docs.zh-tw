---
title: "IRemoteDebugApplicationThread::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetState"
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetState
取得這個執行緒狀態。  
  
## 語法  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### 參數  
 `pState`  
 \[in\] 下列執行緒狀態旗標的組合:  
  
|常數|值|描述|  
|--------|-------|--------|  
|THREAD\_STATE\_RUNNING|0x00000001|執行緒執行。|  
|THREAD\_STATE\_SUSPENDED|0x00000002|執行緒已經暫止。|  
|THREAD\_BLOCKED|0x00000004|執行緒已封鎖。|  
|THREAD\_OUT\_OF\_CONTEXT|0x00000008|執行緒就不是內容。|  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會取得這個執行緒狀態。  
  
## 請參閱  
 [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)