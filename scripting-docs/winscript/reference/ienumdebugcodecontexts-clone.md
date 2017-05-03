---
title: "IEnumDebugCodeContexts::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Clone"
ms.assetid: eaad6af9-4a0a-49c9-8f73-bccaa42b235c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Clone
建立列舉程式，其中包含與目前列舉程式相同的狀態。  
  
## 語法  
  
```  
HRESULT Clone(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### 參數  
 `ppescc`  
 \[in\] 傳回列舉值的 `IEnumDebugCodeContexts` 複製的介面。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會建立包含狀態與目前列舉值相同的列舉值。  
  
## 請參閱  
 [IEnumDebugCodeContexts 介面](../../winscript/reference/ienumdebugcodecontexts-interface.md)