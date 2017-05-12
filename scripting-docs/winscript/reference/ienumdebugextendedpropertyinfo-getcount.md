---
title: "IEnumDebugExtendedPropertyInfo::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.GetCount
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::GetCount"
ms.assetid: 2c862f62-b57c-4cd4-ac4e-7d372fbda9a4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::GetCount
取得 `ExtendedDebugPropertyInfo` 結構數目的列舉值。  
  
## 語法  
  
```  
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### 參數  
 `pcelt`  
 \[in\] 傳回 `ExtendedDebugPropertyInfo` 結構數目的列舉值。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 請參閱  
 [IEnumDebugExtendedPropertyInfo 介面](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)