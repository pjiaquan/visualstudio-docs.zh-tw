---
title: "IDebugApplicationNode::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.Attach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::Attach"
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::Attach
將這個應用程式會為指定的專案樹狀結構。  
  
## 語法  
  
```  
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### 參數  
 `pdanParent`  
 \[in\] 專案樹狀結構中這個應用程式就要加入的。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會將此應用程式會加入至專案樹狀結構中，使用 `pdanParent` 做為父代。  如果 `pdanParent` 是 `NULL`，則應用程式就會是最上層節點。  
  
## 請參閱  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)