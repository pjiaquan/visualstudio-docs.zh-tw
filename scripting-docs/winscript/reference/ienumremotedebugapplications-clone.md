---
title: "IEnumRemoteDebugApplications::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplications.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplications::Clone"
ms.assetid: 762f6dac-1be4-49ec-afda-68c1b29f7a4b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplications::Clone
建立列舉程式，其中包含與目前列舉程式相同的狀態。  
  
## 語法  
  
```  
HRESULT Clone(  
   IEnumRemoteDebugApplications**  ppessd  
);  
```  
  
#### 參數  
 `ppessd`  
 \[in\] 列舉值的複製品。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會建立包含狀態與目前列舉值相同的列舉值。  
  
## 請參閱  
 [IEnumRemoteDebugApplications 介面](../../winscript/reference/ienumremotedebugapplications-interface.md)