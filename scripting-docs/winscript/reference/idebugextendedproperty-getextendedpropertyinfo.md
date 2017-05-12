---
title: "IDebugExtendedProperty::GetExtendedPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::GetExtendedPropertyInfo"
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::GetExtendedPropertyInfo
擷取擴充屬性的擴充資訊，比更簡單的 `IDebugProperty`是詳細資訊。  
  
## 語法  
  
```  
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### 參數  
 `dwFieldSpec`  
 \[in\] 指定判斷在 `ExtendedDebugPropertyInfo` 結構填寫之欄位的 EX\_DBGPROP\_INFO\_FLAGS 常數。  
  
 `nRadix`  
 \[in\] 用來解譯任何數字資訊的基數。  
  
 `pExtendedPropertyInfo`  
 \[in\] 傳回描述屬性的 `ExtendedDebugPropertyInfo` 結構。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 請參閱  
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)