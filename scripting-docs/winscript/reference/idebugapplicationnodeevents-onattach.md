---
title: "IDebugApplicationNodeEvents::onAttach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onAttach
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onAttach"
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onAttach
處理事件表示偵錯應用程式的物件會附加至父節點。  
  
## 語法  
  
```  
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### 參數  
 `prddpParent`  
 \[in\] 是這個節點的父代偵錯應用程式的節點。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會處理事件表示偵錯應用程式的物件會附加至父節點。  
  
 `IDebugApplicationNode` 介面的實作會引發這個事件。  
  
## 請參閱  
 [IDebugApplicationNodeEvents 介面](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)   
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)