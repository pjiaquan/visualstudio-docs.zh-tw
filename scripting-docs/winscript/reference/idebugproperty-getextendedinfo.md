---
title: "IDebugProperty::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetExtendedInfo"
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetExtendedInfo
擴充屬性的資訊。  
  
## 語法  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### 參數  
 `cInfos`  
 \[in\] 計數擴充資訊物件。  
  
 `rgguidExtendedInfo`  
 \[in\] 陣列的 `GUID`傳遞，以便擴充資訊多個項目可以同時擷取。  
  
 `pExtendedInfo`  
 \[in\] 傳回可用來擷取擴充屬性資訊的陣列 `VARIANT`s。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 備註  
 這個介面會擴充這個物件的相關資訊。  API 會提供擷取不本身會擷取使用 `IDebugProperty::GetPropertyInfo`\) 的資訊的目的只存在。  
  
## 請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)