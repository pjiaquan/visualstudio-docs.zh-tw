---
title: "IRemoteDebugApplicationThread::EnumStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.EnumStackFrames
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::EnumStackFrames"
ms.assetid: 605ce83d-43d2-47ea-b066-ec8f0da50ca6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::EnumStackFrames
傳回堆疊框架的列舉值與這個執行緒。  
  
## 語法  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### 參數  
 `ppedsf`  
 \[out\] 堆疊框架的列舉值與這個執行緒。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 必須先呼叫這個方法從中斷點的內部。  堆疊框架列舉值應該傳回開始堆疊最上方的框架，從最近推入的框架開始。  
  
## 請參閱  
 [IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)