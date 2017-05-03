---
title: "IDebugHelper::CreateSimpleConnectionPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreateSimpleConnectionPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreateSimpleConnectionPoint"
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreateSimpleConnectionPoint
傳回指定 `IDispatch` 包裝物件的事件介面。  
  
## 語法  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp   
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### 參數  
 `pdisp`  
 \[out\] `IDispatch` 包裝的物件。  
  
 `ppscp`  
 \[in\] 封裝 `pdisp`的事件介面。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 傳回包裝指定 `IDispatch` 的事件介面 \(請參閱 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)\)。  
  
## 請參閱  
 [IDebugHelper 介面](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint 介面](../../winscript/reference/isimpleconnectionpoint-interface.md)