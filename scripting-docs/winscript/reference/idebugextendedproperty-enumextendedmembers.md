---
title: "IDebugExtendedProperty::EnumExtendedMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.EnumExtendedMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::EnumExtendedMembers"
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::EnumExtendedMembers
列舉型別擴充屬性的成員。  
  
## 語法  
  
```  
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### 參數  
 `dwFieldSpec`  
 \[in\] 指定識別欄位列舉延伸的偵錯屬性結構要填入的 EX\_DBGPROP\_INFO\_FLAGS 常數。  
  
 `nRadix`  
 \[in\] 用來解譯任何數字資訊的基數。  
  
 `ppeepi`  
 \[in\] 傳回列舉型別成員屬性的 `IEnumDebugExtendedPropertyInfo` 介面。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 請參閱  
 [IDebugExtendedProperty 介面](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)