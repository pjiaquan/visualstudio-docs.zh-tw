---
title: "IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:ForceStepMode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:ForceStepMode"
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:ForceStepMode
強制偵錯工具中逐步執行方式。  
  
## 語法  
  
```  
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### 參數  
 `pStepThread`  
 \[in\] 處理序的執行緒偵錯監視器逐步執行。  如果是 null，則 PDM 清除逐步執行執行緒。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/zh-tw/2f65fa67-06b7-4053-8945-22383ab66343)