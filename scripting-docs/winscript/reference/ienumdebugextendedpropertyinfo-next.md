---
title: "IEnumDebugExtendedPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Next"
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Next
擷取`ExtendedDebugPropertyInfo` 結構的指定數目在列舉型別序列的。  
  
## 語法  
  
```  
HRESULT Next (  
   ULONG celt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### 參數  
 `celt`  
 \[in\] `ExtendedDebugPropertyInfo`結構數目要擷取之的。  
  
 `rgelt`  
 \[out\] 指標的陣列擷取的 `ExtendedDebugPropertyInfo` 結構。  
  
 `pceltFetched`  
 \[in\] `ExtendedDebugPropertyInfo` 結構數目實際上已擷取的。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 請參閱  
 [IEnumDebugExtendedPropertyInfo 介面](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)