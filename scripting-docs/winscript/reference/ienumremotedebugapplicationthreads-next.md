---
title: "IEnumRemoteDebugApplicationThreads::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Next"
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Next
`Next` 方法擷取區段的指定數目在列舉型別序列中  
  
## 語法  
  
```  
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### 參數  
 `celt`  
 \[in\] 要擷取的區段數目。  
  
 `pprdat`  
 \[in\] 傳回表示擷取的區段的陣列 `IRemoteDebugApplicationThread` 介面。  
  
 `pceltFetched`  
 \[in\] 列舉值擷取的區段的實際數目。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會擷取區段的指定數目在列舉型別序列中  
  
## 請參閱  
 [IEnumRemoteDebugApplicationThreads 介面](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)