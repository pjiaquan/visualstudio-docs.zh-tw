---
title: "IEnumDebugStackFrames::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Clone"
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Clone
建立列舉程式，其中包含與目前列舉程式相同的狀態。  
  
## 語法  
  
```  
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### 參數  
 `ppedsf`  
 \[in\] 傳回列舉值的 `IEnumDebugStackFrames`複製的介面。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會建立包含狀態與目前列舉值相同的列舉值。  
  
## 請參閱  
 [IEnumDebugStackFrames 介面](../../winscript/reference/ienumdebugstackframes-interface.md)